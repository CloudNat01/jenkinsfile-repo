pipeline {
    agent any
    
    stages {
        stage("Git Checkout") {
            steps {
                git 'https://github.com/CloudNat01/jenkinsfile-repo.git'
            }
        }
        stage("Docker login") {
            steps {
                withCredentials([string(credentialsId: 'DOCKERHUB_TOKEN', variable: 'DOCKERHUB_TOKEN'), string(credentialsId: 'DOCKERHUB_USERNAME', variable: 'DOCKERHUB_USERNAME')]) {
                    sh '''
                        echo $DOCKERHUB_TOKEN | docker login -u $DOCKERHUB_USERNAME --password-stdin
                    '''
                }
            }
        }
        stage("Docker build") {
            steps {
                sh 'docker build -t $DOCKERHUB_USERNAME/pipelineb-img:latest .'
            }
        }
        stage("Docker push") {
            steps {
                sh 'docker push $DOCKERHUB_USERNAME/pipelineb-img:latest'
            }
        }
    }
}
