pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                sh 'git branch: 'main', url:git@github.com:gummallasainathreddy/jenkins-docker.git'
            }
        }
         stage('install docker') {
            steps {
                sh 'sudo yum install docker -y'
                sh 'sudo systemctl start docker'
                sh 'sudo systemctl enable docker'
            }
        }
         stage('Docker login') {
            steps {
                sh 'aws ecr get-login-password --region eu-west-2 | sudo docker login --username AWS --password-stdin 101275806917.dkr.ecr.eu-west-2.amazonaws.com'
            }
        }
        stage('build') {
            steps {
                sh 'sudo docker build -t docker tag 101275806917.dkr.ecr.eu-west-2.amazonaws.com/ecr-docker:latest .'
            }
        }
        stage('push') {
            steps {
                sh 'sudo docker push 101275806917.dkr.ecr.eu-west-2.amazonaws.com/ecr-docker:latest'
            }
        }
    }
}
