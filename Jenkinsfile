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
        sh 'docker run -p 8090:8080 -d --name test_jenkins my_server:latest'
        sh '[ "This is my super app" = "$(curl http://localhost:8080/)" ]'
        sh 'docker rm -f test_jenkins'
      }
    }
  }
  post {
    always {
      sh 'docker rm -f test_jenkins'
    }
  }
}
