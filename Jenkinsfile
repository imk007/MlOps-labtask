pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/AsimAltaf-eg/flask-app.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker image build -t my-app .'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 my-app'
            }
        }
        stage('Test API') {
            steps {
                sh 'python request.py'
            }
        }
        stage('Stop Container') {
            steps {
                sh 'docker stop $(docker ps -q)'
            }
        }
    }
}
