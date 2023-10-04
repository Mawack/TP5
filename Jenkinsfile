pipeline {
  agent {
    label 'docker'
  }
  stages {
    stage('Docker build') {
      steps {
        sh 'docker build -t my_server:latest - < Dockerfile'
        sh 'docker images'
      }
    }
    stage ('Test image') {
      steps {
        sh 'docker run -p 8080:8090 -d --name docker image:tag'
        sh '[ "This is my super app" = "$(curl http://localhost:8090/)" ]'
        sh 'docker rm -f test_jenkins'
      }
    }
  }
}
