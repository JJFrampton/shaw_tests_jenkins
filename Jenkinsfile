pipeline {
    agent { docker { image 'node:6.3' } }
    parameters {
        string(defaultValue: 'master', description: 'which branch to run', name: 'branch')
    }
    stages {
        stage('build') {
            steps {
                sh "npm --version"
                sh "echo 'BRANCH : ${params.branch}'"
            }
        }
    }
    post {
      always {
          sh "echo 'cleaning workspace'"
      }
    }
}
