pipeline {
    environment {
        registry = "utkarsh12/cyberfrat-devsecops"
        registryCredential= "60fd5250-e98d-4695-90ae-6a46a710f230"
        dockerImage= ''
    }
    
    agent any
    
      stages {
        stage('Build Docker Image') {
          steps {
              script {
                  dockerImage = docker.build registry + ":$BUILD_NUMBER"
              }
             }
            }
          stage('Push to DockerHub') {
              steps {
                  script {
                  docker.withRegistry('',registryCredential ) {
                      dockerImage.push()
                  }
              }
              }
          }
          stage('Test Run') {
          steps {
              sh 'docker run -d $registry:$BUILD_NUMBER'
          }
      }      
   }
 }
             
