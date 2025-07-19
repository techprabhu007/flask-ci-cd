pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/techprabhu007/flask-ci-cd.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true
                docker run -d -p 5000:5000 --name flask-container flask-app
                '''
            }
        }
    }
}
