pipeline {
    environment {
        IMAGE_NAME = "alok4697/devops"
        dockerHubCredentials = 'admins'
        TAG = 'jb-${BUILD_NUMBER}'
        
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
                     sh "sudo docker build -t ${IMAGE_NAME}:${TAG} ."
                     echo "Docker build succeeded"
                }
            }
 
         stage('Docker Image Push') {
             steps {
                script {
           
                    withCredentials([usernamePassword(credentialsId: dockerHubCredentials, usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
 
                        
                        sh "docker push ${IMAGE_NAME}:${TAG}"
                        echo "Docker Image push Successfull"
                    }
             }

        }
    }  
  }
}
