pipeline {
  agent {
    node {
      label 'Docker-slave'
    }

  }
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/Foondel/node-hello.git', branch: 'master', changelog: true, poll: true)
      }
    }

  }
}