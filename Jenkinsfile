pipeline {
    environment {
        IMAGE_NAME = "alok4697/devops"
        Docker_Regitry = 'docker.io/alok4697/devops'
        USR = 'alok4697'
        PWD = 'Aloksingh@1997'
        
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
           
                    withCredentials([usernamePassword(credentialsId: admins, usernameVariable: 'USR', passwordVariable: 'PWD')]) {
                        sh "docker login -u $USR -p $PWD"
 
                        
                        sh "docker push ${Docker_Regitry}/${IMAGE_NAME}:latest"
                        echo "Docker Image push Successfull"
                    }
             }

        }
    }  
  }
}
