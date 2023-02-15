pipeline {
    agent any
    stages {
        stage('Code checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '23fdc10b-169b-47f7-b512-1e74bb463b0c', url: 'https://github.com/SharanyaJayaram/htmlsample.git']])
            }
        }
        stage('Docker Build image') {
            steps {
                script{
                    sh 'docker build -t htmlimage .'
                }
            }
        }
        stage('Push Image to Dockerhub') {
            steps {
               withCredentials([usernamePassword(credentialsId: 'DockerDemo', passwordVariable: 'DockerDemoPassword', usernameVariable: 'DockerDemoUser')]) {
            sh 'docker login -u ${env.DockerDemoUser} -p ${env.DockerDemoPassword}'
            sh 'docker tag htmlimage:latest shrth7/devops:latest'
            sh 'docker push shrth7/devops:latest'
            }
            }
        }
    }
}
