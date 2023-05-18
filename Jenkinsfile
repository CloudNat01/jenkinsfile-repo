pipeline{
    agent any
    // environment {     
    //         DOCKERHUB_CREDENTIALS= credentials('dockerhubcreds')     
    //     }
    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/CloudNat01/jenkinsfile-repo.git'
            }
        }
        stage("Docker login"){
            steps{
                withCredentials([string(credentialsId: 'DOCKERHUB_TOKEN', variable: 'DOCKERHUB_TOKEN'), string(credentialsId: 'DOCKERHUB_USERNAME', variable: 'DOCKERHUB_USERNAME')]) {
                    sh ' docker login -u \'$DOCKERHUB_USERNAME\' --password-stdin \'$DOCKERHUB_TOKEN\''
              }
                
            }
        }
        stage("docker build"){
            steps{
                sh 'docket build -t $DOCKERHUB_USERNAME/pipelineb-img:latest .'
            }
        }
        stage("Docker push"){
            steps{
                sh 'docket push $DOCKERHUB_USERNAME/pipelineb-img:latest'
            }
        }
    }
  
}
