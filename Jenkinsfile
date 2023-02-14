pipeline {
    agent any
    stages{
        stage("ECR login"){
            steps{
            sh 'aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/s2l4n6u7'
            }
        }
        
        stage("Build image"){
            steps{
            sh 'docker build -t registry2 .'
            }
        }
        
        stage("Adding tag"){
            steps{
            sh 'docker tag registry2:latest public.ecr.aws/s2l4n6u7/registry2:latest'
            }
        }
        
        stage("Pushing the image"){
            steps{
            sh 'docker push public.ecr.aws/s2l4n6u7/registry2:latest'
            }
        }
    }
}
