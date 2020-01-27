pipeline {
    agent { docker { image 'node:6.3' } }
    environment {

    }
    options {
        timestamps()
    }
    parameters {
        string(defaultValue: 'master', description: 'which branch to run', name: 'branch')
        string(defaultValue: 'master', description: 'which branch to run', name: 'branch2')
    }
    stages {
        stage('build') {
            steps {
                sh "./build.sh"
                sh "npm --version"
                sh "echo 'PARAMS : ${params}'"
            }
        }
    }
    post {
      always {
          sh "Post-Processing"
          /* archiveArtifacts artifacts: '${ARTIFACTS}', allowEmptyArchive: false */
          cleanWs()
      }
    }
}
