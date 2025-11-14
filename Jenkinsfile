pipeline {
  agent any

  environment {
    DOCKERHUB_CREDENTIALS = 'dockerhub-creds'
    IMAGE_NAME = "nodejs-demo-app"
    DOCKERHUB_USER = "<your-dockerhub-username>"
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Build') {
      steps {
        sh 'npm ci'
        sh 'npm test || true'
      }
    }
    stage('Docker Build') {
      steps {
        sh "docker build -t ${DOCKERHUB_USER}/${IMAGE_NAME}:latest ."
      }
    }
    stage('Docker Login & Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: "${DOCKERHUB_CREDENTIALS}", passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
          sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
          sh "docker push ${DOCKERHUB_USER}/${IMAGE_NAME}:latest"
        }
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
