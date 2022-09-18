pipeline {
    agent any

    environment {
        REGISTRY_URL = "352708296901.dkr.ecr.eu-north-1.amazonaws.com"
        IMAGE_TAG = "0.0.$BUILD_NUMBER"
        IMAGE_NAME = "alonit-bot"
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 352708296901.dkr.ecr.eu-central-1.amazonaws.com
                docker build -t elkan316 .
                docker tag elkan316:latest 352708296901.dkr.ecr.eu-central-1.amazonaws.com/elkan316:latest
                docker push 352708296901.dkr.ecr.eu-central-1.amazonaws.com/elkan316:latest
                '''
            }
        }
        stage('Trigger Deploy') {
            steps {
                build job: "BotDeploy", wait: false, parameters: [
                    string(name: 'BOT_IMAGE', value: "${REGISTRY_URL}/${IMAGE_NAME}:${IMAGE_TAG}")
                ]
            }
        }
    }
}