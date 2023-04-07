pipeline {
  agent any
  stages {
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
