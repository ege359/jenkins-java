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

    stage('Compile Java Code') {
      steps {
        script {
          sh 'javac YourJavaFile.java'
        }

      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f Dockerfile . -t ege359/jenkins-project:latest'
      }
    }

    stage('DockerHub') {
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push ') {
      steps {
        sh 'docker push ege359/jenkins-project:latest'
      }
    }

  }
  environment {
    DOCKERHUB_USER = 'ege359'
    DOCKERHUB_PASSWORD = 'egebatu2000'
  }
}