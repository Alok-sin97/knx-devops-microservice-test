pipeline {
    environment {
        imagename = "devops"
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
        }
    }
