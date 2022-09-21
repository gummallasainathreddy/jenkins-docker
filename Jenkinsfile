pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                sh 'git clone git@github.com:gummallasainathreddy/jenkins-docker.git'
            }
        }
         stage('install docker') {
            steps {
                sh 'sudo yum install docker -y'
                sh 'sudo systemctl start docker'
                sh 'sudo systemctl enable docker'
            }
        }
         stage('build image') {
            steps {
                sh 'sudo docker -t apacheimage:$BUILD_NUMBER .'
            }
        }
    }
}
