pipeline {
    agent { docker { image 'node:6.3' } }
    parameters {
        string(defaultValue: 'master', description: 'which branch to run', name: 'branch')
        string(defaultValue: 'master', description: 'which branch to run', name: 'branch2')
    }
    stages {
        stage('build') {
            steps {
                sh "npm --version"
                sh "echo 'PARAMS : ${params}'"
            }
        }
    }
    post {
      always {
          sh "echo 'cleaning workspace for ${params.branch}'"
      }
    }
}
