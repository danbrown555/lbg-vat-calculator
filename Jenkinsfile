pipeline {
  agent any

  stages {
    stage('Checkout') {
        steps {
          // Gets some code from a GitHub repositoryxxxxs
          git branch: 'main', url: 'https://github.com/danbrown555/lbg-vat-calculator.git'
        }
    }
    stage('SonarQube Analysis') {
      environment {
        scannerHome = tool 'sonarqube'
      }
        steps {
            withSonarQubeEnv('sonar-qube-1') {        
              sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES'){
          waitForQualityGate abortPipeline: true
        }
    }
  }
}
}
