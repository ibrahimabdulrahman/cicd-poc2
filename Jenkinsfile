pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t simple-poc:latest .'
      }
    }

    stage('Deploy Container') {
      steps {
        sh '''
          docker rm -f simple-poc || true
          docker run -d --name simple-poc -p 80:8080 simple-poc:latest
        '''
      }
    }
  }
}
