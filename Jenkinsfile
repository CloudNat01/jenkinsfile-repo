pipeline{
    agent any
    stages{
        stage("Git Checkout"){
            steps{
                git 'https://github.com/CloudNat01/jenkinsfile-repo.git'
            }
        }
        stage("Docker login"){
            steps{
                sh 'echo $DOCKERHUB_PASSWORD  | docker login -u $DOCKERHUB_USERNAME --password-stdin'
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