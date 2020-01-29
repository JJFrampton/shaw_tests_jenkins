pipeline {
    agent any

    environment {
        PROJECT = 'wifi'
    }

    triggers {
        pollSCM('H H(0-2) * * *')    //Should use a git hook to build on change?
    }

    options {
        buildDiscarder(logRotator(numToKeepStr:'3'))    //How many builds to keep in history
        timestamps()
    }

    stages {
        stage('Params') {
            steps {
                sh "# target_project : ${PROJECT}"
            }
        }
        stage('Build') {
            steps {
                sh "# Building ${PROJECT}"
                sh "./build.sh"
                sh "docker tag ${PROJECT}:latest ${PROJECT}:\$(date '+%F')"
                sh "docker save ${PROJECT}:\$(date '+%F') > ${PROJECT}-\$(date '+%F').tar"
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '${PROJECT}-*', allowEmptyArchive: false
            cleanWs()
        }
    }
}
