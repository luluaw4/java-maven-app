pipeline {
    agent any
    environment {
        DOCKER_CREDENTIALS = credentials('dockerhub-token')  // Use your credentials ID
    }
    stages {
        stage('Docker Login') {
            steps {
                script {
                    sh 'echo $DOCKER_CREDENTIALS_PSW | docker login -u $DOCKER_CREDENTIALS_USR --password-stdin'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t luluaw4/demo-app:jma-1.0 .'
            }
        }
    }
}
