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

    stage('Build') {
      steps {
        sh 'docker build -f Dockerfile .'
      }
    }

    stage('DcockerHub') {
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push ') {
      steps {
        sh 'docker push jenkins-project:latest'
      }
    }

  }
  environment {
    DOCKERHUB_USER = 'ege359'
    DOCKERHUB_PASSWORD = 'egebatu2000'
  }
}