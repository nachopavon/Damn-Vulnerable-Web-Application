pipeline {
  agent any
  stages {
    stage('SonarQube analysis') {
      steps {
        script {
          def scannerHome = tool 'sonarqube';
          withSonarQubeEnv('sonarqube') {
            sh "${tool("sonarqube")}/bin/sonar-scanner -Dsonar.projectKey=dvwa -Dsonar.projectName=DVWA"
          }
        }

      }
    }

    stage('') {
      steps {
        waitForQualityGate true
      }
    }

  }
  environment {
    projectName = 'dvwa'
  }
}