pipeline {
  agent any
  stages {
    stage('sonar') {
      steps {
        withSonarQubeEnv('sonarqube') {
          waitForQualityGate true
        }

      }
    }

  }
  environment {
    projectName = 'dvwa'
  }
}