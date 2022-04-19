pipeline {
    agent any
    environment {
        projectName = "dvwa"
    }

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
  }
}
