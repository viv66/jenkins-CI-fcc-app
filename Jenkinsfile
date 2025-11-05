pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/viv66/jenkins-CI-fcc-app', branch: 'master')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile -t fuze365/curriculum-front:latest'
      }
    }

    stage('Log into Docker Hub') {
      environment {
        DOCKERHUB_USER = '586958'
        DOCKERHUB_PASSWORD = 'dbt38EmV$$'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push fuze365/curriculum-front:latest'
      }
    }

  }
}