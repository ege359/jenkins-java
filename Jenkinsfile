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
          sh 'javac basic-java.java'
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

    stage('Deploy to Server') {
      steps {
        script {
          sshagent(['ssh']) {
            sh 'ssh egedocker@192.168.109.131 "docker pull ege359/jenkins-project:latest && docker run -d --name jenkins-project -p 8080:80 ege359/jenkins-project:latest"'
          }
        }

      }
    }

  }
  environment {
    DOCKERHUB_USER = '@'
    DOCKERHUB_PASSWORD = '@'
  }
}
