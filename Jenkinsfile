pipeline {
    agent { docker { image 'node:6.3' } }

    parameters {
        string(name: 'target_project', defaultValue: 'captive-portal', description: 'project to build', trim: true)
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
            sh "echo 'target_project : ${params.target_project}'"
        }
        stage('Build') {
            steps {
                sh "echo 'Building ${params.target_project}'"
                sh "./build.sh"
                sh "docker tag ${params.target_project}:latest ${params.target_project}:\$(date '+%F')"
                sh "docker save ${params.target_project}:\$(date '+%F') > ${params.target_project}-\$(date '+%F').tar"
            }
        }
        stage('Test') {
            steps {
                sh "echo 'Test not implemented for ${params.target_project}'"
            }
        }
        stage('Deploy') {
            steps {
                sh "echo 'Deploy not implemented for ${params.target_project}'"
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '${params.target_project}-*', allowEmptyArchive: false
            cleanWs()
        }
    }
}
