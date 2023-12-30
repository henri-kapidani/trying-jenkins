pipeline {
  agent any
  stages {
    stage('checkout code') {
      steps {
        git(url: 'https://github.com/henri-kapidani/trying-jenkins', branch: 'main')
      }
    }

    stage('Log') {
      parallel {
        stage('Log') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Front-End Unit Tests') {
          steps {
            sh 'cd curriculum-front && npm i && npm run test:unit'
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Docherfile .'
      }
    }

    stage('Login to Dockerhub') {
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile . -t asdf/asdfsadfsdf:latest'
      }
    }

  }
  environment {
    DOCKERHUB_USER = 'ASDF'
    DOCKERHUB_PASSWORD = 'ZXCV'
  }
}