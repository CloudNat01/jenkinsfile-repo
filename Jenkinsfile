pipeline{
    agent any
    environment {     
            DOCKERHUB_CREDENTIALS= credentials('dockerhubcreds')     
        }
    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/CloudNat01/jenkinsfile-repo.git'
            }
        }
        stage("Docker login"){
            steps{
                sh 'echo \'$DOCKERHUB_CREDENTIALS_PSW\'  | docker login -u \'$DOCKERHUB_USERNAME_USR\' --password-stdin'
            }
        }
        stage("docker build"){
            steps{
                sh 'docket build -t $DOCKERHUB_USERNAME/pipeline-img:latest .'
            }
        }
        stage("Docker push"){
            steps{
                sh 'docket push $DOCKERHUB_USERNAME/pipeline-img:latest'
            }
        }
    }
  
}