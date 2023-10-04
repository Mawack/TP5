pipeline {
  agent {
    label 'docker'
  }
  stages {
    stage('init') {
      steps {
        sh 'docker run hello-world'
      }
    }
  }
}
