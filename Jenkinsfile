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
        sh '[ "This is my super app" = "$(curl http://57.128.61.129:8090/)" ]'
      }
    }
    stage ('MEP') {
      steps {
        sh 'docker-compose up -d --force-recreate'
      }
    }
  }
  post {
    always {
      # sh 'docker rm -f test_jenkins'
    }
  }
}
