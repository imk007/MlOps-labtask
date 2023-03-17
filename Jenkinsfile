pipeline {
  agent {
    docker {
      image 'python:3.8-slim-buster'
      args '--user 1000:1000 --entrypoint sh'
    }
  }
  
  stages {
    stage('Build') {
      steps {
        sh 'pip install -r requirements.txt'
        sh 'docker image build -t myapp .'
      }
    }
    
    stage('Deploy') {
      steps {
        sh 'docker run -p 5000:5000 myapp'
      }
    }
  }
}
