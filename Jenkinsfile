pipeline {
  agent any
  stages {
    stage('BUILD') {
      agent {
        docker {
          image 'node:6-alpine'
          args '-p 3000:3000'
        }

      }
      steps {
        sh 'npm install'
      }
    }
    stage('TEST') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('DELIVER') {
      steps {
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}