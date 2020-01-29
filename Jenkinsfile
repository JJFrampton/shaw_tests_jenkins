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
                sh "./build.sh"
                /* sh "docker tag ${PROJECT}:latest ${PROJECT}:\$(date '+%F')" */
                /* sh "docker save ${PROJECT}:\$(date '+%F') > ${PROJECT}-\$(date '+%F').tar" */
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: "${PROJECT}-*", allowEmptyArchive: false
            cleanWs()
        }
    }
}
