pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'npm install'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        bat './scripts/test.bat'
      }
    }
    stage('Deliver') {
      steps {
        bat './scripts/deliver.bat'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        bat './scripts/kill.bat'
      }
    }
  }
}