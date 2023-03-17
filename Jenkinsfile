pipeline {
    agent any
    
    stages {
        stage('Build Docker image') {
            steps {
                script {
                    docker.build("my-app:latest", ".")
                }
            }
        }
        
        stage('Run Docker container') {
            steps {
                script {
                    docker.run("my-app:latest", "-p 5000:5000")
                }
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        
        failure {
            echo 'Pipeline failed.'
        }
    }
}
