pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/ege359/jenkins-java', branch: 'main', credentialsId: '1', poll: true)
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('docker') {
      steps {
        sh 'docker build -f /var/lib/docker/overlay2/kvmhci1jo8w0rweerr4oostts/diff/Dockerfile .'
      }
    }

  }
}