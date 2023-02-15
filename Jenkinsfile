pipeline {
    agent any
    stages {
        stage('Login') {
            steps {
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 210866101523.dkr.ecr.us-east-1.amazonaws.com'
            }
        }
        stage('Build image and tag') {
            steps {
                script{
                    sh 'docker build -t registry .'
                    sh 'docker tag registry:latest 210866101523.dkr.ecr.us-east-1.amazonaws.com/registry:latest'
                }
            }
        }
        stage('Push Image') {
            steps {
               sh 'docker push 210866101523.dkr.ecr.us-east-1.amazonaws.com/registry:latest'
                }
            
            
            
            }
        }
    }

