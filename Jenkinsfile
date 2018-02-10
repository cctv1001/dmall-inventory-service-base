pipeline {
    agent any

    triggers{
        pollSCM('*****')
    }

   environment{
    DMALL_DOCKER_REGISTRY='ec2-54-95-48-23.ap-northeast-1.compute.amazonaws.com:5000'
    SLUG='guyumei-space'
   }

    stages {
        stage('Build') {
            steps{
                sh './gradlew build'
                sh 'ls build/libs'
            }
        }

        stage('Docker image') {
            steps{
                sh 'echo "image"'
            }
        }

        stage('Deploy to DEV') {
            steps{
                withCredentials([[$class: 'FileBinding', credentialsId: 'kubectl-config-file', variable: 'KUBECTL_CONFIG_FILE']]) {
                    sh 'echo "deploy"'
                }
            }
        }
    }
}