pipeline {
  agent {
    label 'docker'
  }
  stages {
    stage('Docker build') {
      steps {
        sh 'docker build -t my_server:latest - < Dockerfile'
      }
    }
  }
}
