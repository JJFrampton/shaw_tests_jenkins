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
                sh "pwd"
                sh "git clone http://10.9.75.33:3000/jframpton/localtest.git"
                sh "./build.sh"
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
