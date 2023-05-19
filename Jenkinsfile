pipeline {
    agent any
    
    environment {
        DOCKERHUB_USERNAME = credentials('dockerhub-creds').username
        DOCKERHUB_PASSWORD = credentials('dockerhub-creds').password
    }
    
    stages {
        stage('Build and push Docker image') {
            steps {
                sh "docker build -t myimage:${BUILD_NUMBER} ."
                sh "echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin"
                sh "docker tag myimage:${BUILD_NUMBER} myusername/myimage:${BUILD_NUMBER}"
                sh "docker push myusername/myimage:${BUILD_NUMBER}"
            }
        }
    }
}
