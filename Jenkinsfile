node('master') {
    try {
        stage 'Checkout'
            checkout scm
        stage 'Version Check'
            sh 'npm --version'
            sh 'phantomjs -v'
        stage 'Set Npm Prefix'
            sh 'npm config set prefix ~/mutable_node_modules'
        stage 'Dependencies'
            sh 'npm uninstall phantomjs-prebuilt'
            sh 'npm install bower'
            sh 'npm install -g bower'
            sh 'npm install gulp'
            sh 'npm install -g gulp'
        stage 'Node Build'
            env.PATH = "~/mutable_node_modules/bin/:${env.PATH}"
            sh 'npm install'
            sh 'bower install'
            sh 'cd test && bower install && cd ../'
        stage 'gulp build'
            env.PATH = "~/mutable_node_modules/bin/:${env.PATH}"
            sh 'gulp build'
        currentBuild.result = "SUCCESS"
    } catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }
}
