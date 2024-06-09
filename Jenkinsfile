pipeline {
    environment {
        imagename = "devops"
        USR = "alok4697"
        PWD = "Aloksingh@1997"
        
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
                     sh "sudo docker build -t ${imagename}:latest ."
                     echo "Docker build succeeded"
                }
            }
 
         stage('Docker Image Push') {
             steps {
                script {
                    // Use Jenkins credentials for Docker Hub login
                    withCredentials([usernamePassword(credentialsId: dockerHub, usernameVariable: 'USR', passwordVariable: 'PWD')]) {
                        sh "docker login -u $USR -p $PWD"
 
                        // Push the image
                        sh "docker push ${imagename}:latest"
                    }
             }

        }
    }  
  }
}
