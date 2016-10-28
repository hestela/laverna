node('master') {
    try {
        stage 'Checkout'
            checkout scm
        stage 'Version Check'
            sh 'npm --version'
        stage 'Set Npm Prefix'
            sh 'npm config set prefix ~/mutable_node_modules'
        stage 'Dependencies'
            sh 'npm install -g gulp bower'
            sh 'npm install gulp bower'
        stage 'Node Build'
            env.PATH = "~/mutable_node_modules/bin/:${env.PATH}"
            sh 'npm install'
            sh 'bower install'
            sh 'cd test && bower install && cd ../'
        currentBuild.result = "SUCCESS"
    } catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }
}
