pipeline {
  agent {
      node {
          label 'kubeagent'
      }
  }

  parameters {
    string(
        name: "Branch_Name", 
        defaultValue: 'main', 
        description: '')
        string(
          name: "Image_Name", 
          defaultValue: 'web', 
          description: '')
        string(
          name: "Image_Tag", 
          defaultValue: '$BUILD_NUMBER', 
          description: '')
      booleanParam(
          name: "PushImage", 
          defaultValue: false)
  }

  stages {// stage blocks
    stage("Build docker images") {
        steps {
          script {
              echo "Bulding docker images"
              def buildArgs = """\
-f ./web/Dockerfile \
./web/"""
              docker.build(
                  "${params.Image_Name}:${params.Image_Tag}",
                  buildArgs)
          }
        }
    }
  }

  // stages {
  //   stage('Install Docker') {
  //     steps {
  //       sh 'apt-get update && apt-get upgrade -y && apt-install docker.io -y'
  //     }
  //   }
  //   stage('Build') {
  //     steps {
  //       sh 'docker build -t localhost:32000/web:$BUILD_NUMBER -f ./web/Dockerfile ./web/'
  //     }
  //   }
  //   stage('Push') {
  //     steps {
  //       sh 'docker push localhost:32000/web:$BUILD_NUMBER'
  //     }
  //   }
  // }
  // post {
  //   always {
  //     sh 'docker rmi localhost:32000/web:$BUILD_NUMBER'
  //   }
  // }
}
