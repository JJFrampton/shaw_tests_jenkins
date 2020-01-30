pipeline {
    agent any

    environment {
        PROJECT = 'wifi'
    }

    options {
        buildDiscarder(logRotator(numToKeepStr:'3'))    //How many builds to keep in history
        timestamps()
    }

    stages {
        stage('Build') {
            steps {
                sh "echo 'PROJECT: ${PROJECT}'"
                /* sh "./build.sh" */
                sh "ls -lah"
                sh "ls -lah ../"
                sh "ls -lah ../localtest_master"
            }
        }
    }

    post {
        always {
            /* archiveArtifacts artifacts: "${PROJECT}-*", allowEmptyArchive: false */
            cleanWs()
        }
    }
}
