pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'docker image build -t my-app .'
            }
        }
        stage('Run') {
            steps {
                sh 'docker run -d -p 5000:5000 my-app'
            }
        }
    }
}
