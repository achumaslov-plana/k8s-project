pipeline {
  agent any
  stages {
    stage('Install Docker') {
      steps {
        sh 'sudo apt-get update && sudo apt-get upgrade -y && sudo apt-install docker.io -y'
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t localhost:32000/web:$BUILD_NUMBER -f ./web/Dockerfile ./web/'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push localhost:32000/web:$BUILD_NUMBER'
      }
    }
  }
  post {
    always {
      sh 'docker rmi localhost:32000/web:$BUILD_NUMBER'
    }
  }
}
