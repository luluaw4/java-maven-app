pipeline {
  agent any

  environment {
    IMAGE_NAME = "luluaw4/demo-app:jma-1.0"
  }

  stages {
    stage('Build') {
      steps {
        sh 'mvn package'
        sh 'docker build -t $IMAGE_NAME .'
      }
    }
    
    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', 
                                          usernameVariable: 'DOCKER_USERNAME', 
                                          passwordVariable: 'DOCKER_PASSWORD')]) {
          sh 'echo $DOCKER_PASSWORD | docker login -u $DOCKER_USERNAME --password-stdin'
          sh 'docker push $IMAGE_NAME'
        }
      }
    }
  }
}
