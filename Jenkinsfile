pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'npm install'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          environment {
            CI = 'true'
          }
          steps {
            bat './scripts/test.bat'
          }
        }
        stage('') {
          steps {
            SoapUIPro(pathToTestrunner: 'C:\\Program Files\\SmartBear\\ReadyAPI-2.4.0\\bin', pathToProjectFile: 'C:\\Users\\michael.hawley\\AppData\\Roaming\\Microsoft\\Windows\\Network Shortcuts\\OpenWeatherAPI-readyapi-project.xml', testSuite: 'OpenWeatherMapAPI TestSuite', testCase: '/weather TestCase', environment: 'Default environment', projectPassword: ' ')
          }
        }
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