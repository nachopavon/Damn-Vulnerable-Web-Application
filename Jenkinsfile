pipeline {
  agent any
  stages {
    stage('Sonarqube') {
      environment {
        scannerHome = 'sonarqube'
      }
      steps {
        withSonarQubeEnv('sonarqube') {
          sh "${scannerHome}/bin/sonar-scanner \
                                               -Dsonar.projectKey=dvwa \
                                               -Dsonar.projectName=DVWA \
                                               -Dsonar.login=$SONAR_AUTH_TOKEN"
        }

        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate true
        }

      }
    }

  }
  environment {
    projectName = 'dvwa'
  }
}