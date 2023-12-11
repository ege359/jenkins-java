pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/ege359/jenkins-java', branch: 'main', credentialsId: '1', poll: true)
      }
    }

  }
}