pipeline {
  agent {
    docker {
      image 'node:16'
      args '''-p 3000:3000
-u root:root'''
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''chown -R 131:139 "/.npm" || true
npm cache clean --force
npm install'''
      }
    }

    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Select "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }

  }
  environment {
    CI = 'true'
  }
}