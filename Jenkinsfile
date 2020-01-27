pipeline {
    agent { docker { image 'node:6.3' } }
    environment {
        ARTIFACTS = 'yoshida'
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
                /* sh "./build.sh" */
                sh "echo 'RUNNING BUILD'"
                sh "npm --version"
                sh "echo 'PARAMS : ${params}'"
            }
        }
        stage('test') {
            steps {
                /* sh "./test.sh" */
                sh "echo 'RUNNING TESTS'"
                sh "npm --version"
                sh "echo 'PARAMS : ${params}'"
            }
        }
    }
    post {
      always {
          sh "echo Post-Processing"
          /* archiveArtifacts artifacts: '${ARTIFACTS}', allowEmptyArchive: false */
          cleanWs()
      }
      /* success { */
      /*     slackSend channel: '#jenkins-test', */
      /*     color: 'good', */
      /*     message: "The pipeline ${currentBuild.fullDisplayName} completed successfully." */
      /* } */
    }
}
