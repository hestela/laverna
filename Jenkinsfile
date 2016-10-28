node('master') {
    try {
        stage 'Checkout'
            checkout scm
        stage 'Version Check'
            sh 'npm --version'
        stage 'Dependencies'
            sh 'npm install -g gulp bower jshint'
        stage 'Node Build'
            sh 'npm install'
            sh 'bower install'
            sh 'cd test && bower install && cd ../'
        stage 'gulp build'
            sh 'gulp build'
        currentBuild.result = "SUCCESS"
    } catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }
}
