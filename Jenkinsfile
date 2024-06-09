pipeline {
    environment {
        IMAGE_NAME = "alok4697/devops"
        DOCKER_USERNAME = "alok4697"
        DOCKER_PASSWORD = "Aloksingh@1997"
    }
 
    agent any
 
    stages {
        stage('Cloning Git') {
            steps {
                git([url: 'https://github.com/Alok-sin97/knx-devops-microservice-test.git', branch: 'main'])
            }
        }
 
        stage('Building image') {
            steps {
                     sh "sudo docker build -t ${IMAGE_NAME}:latest ."
                     echo "Docker build succeeded"
                }
            }
 
         stage('Docker Image Push') {
             steps {
                script {
                    // Use Jenkins credentials for Docker Hub login
                    withCredentials([usernamePassword(credentialsId: docker, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
 
                        // Push the image
                        sh "docker push ${imagename}:latest"
                    }
             }

        }
    }  
  }
}
