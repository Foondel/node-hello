pipeline {
  agent {
    node {
      label 'Docker-Slave'
    }

  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/Foondel/node-hello.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build . -t node-hello:$BUILD_ID'
      }
    }

    stage('Push Docker Image') {
      steps {
        withDockerRegistry(credencialsId: 'docker-hub-creds' , url: 'https://registry.hub.docker.com') {
        sh '''docker tag node-hello:$BUILD_ID foondel/node-hello:$BUILD_ID && docker push foondel/node-hello:$BUILD_ID'''
        }
      }
    }

  }
}
