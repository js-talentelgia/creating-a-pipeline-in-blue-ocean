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

  }
}