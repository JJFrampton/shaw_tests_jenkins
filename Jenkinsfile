pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sh 'whoami'
                sh 'echo params'
            }
        }
    }
}
