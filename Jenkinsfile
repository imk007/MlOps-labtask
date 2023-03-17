pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Clone the repository
                git 'https://github.com/AsimAltaf-eg/flask-app.git'

                // Build the Docker image
                sh 'docker image build -t my-app .'
            }
        }

        stage('Run') {
            steps {
                // Run the Docker container in the background
                sh 'docker run -d -p 5000:5000 my-app start python server.py'

                // Wait for the application to start
                sh 'sleep 10'

                // Test the API endpoint
                sh 'python request.py'
            }
        }
    }

    post {
        always {
            // Stop and remove the Docker container
            sh 'docker stop $(docker ps -q --filter ancestor=my-app) || true'
            sh 'docker rm $(docker ps -aq --filter ancestor=my-app) || true'
        }
    }
}
