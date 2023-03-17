pipeline {
  agent any

  stages {
    stage('Build Docker image') {
      steps {
        script {
          docker.build("my-app")
        }
      }
    }

    stage('Run Docker container') {
      steps {
        script {
          docker.image("my-app").run("-p 5000:5000")
        }
      }
    }
  }
}
