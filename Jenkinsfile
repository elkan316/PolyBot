pipeline {
    agent any


    stages {
        stage('Build') {
            steps {
                sh '''
                aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 352708296901.dkr.ecr.eu-central-1.amazonaws.com
                docker build -t elkan316:0.0.$BUILD_NUMBER .
                docker tag elkan316:0.0.$BUILD_NUMBER 352708296901.dkr.ecr.eu-central-1.amazonaws.com/elkan316:0.0.$BUILD_NUMBER
                docker push 352708296901.dkr.ecr.eu-central-1.amazonaws.com/elkan316:0.0.$BUILD_NUMBER
                '''
             }
        }
        stage('Stage II') {
            steps {
                sh 'echo "stage II Done..."'
                }
            }
            stage('Stage III Done') {
            steps {
                sh 'echo "stage III..."'
        }
    }
}
}
