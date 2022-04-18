pipeline {
    agent any
    environment {
        projectName = "dvwa"
    }

stages {
    stage('Sonarqube') {
    environment {
        scannerHome = tool 'sonarqube'
    }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner \
                 -Dsonar.projectKey=dvwa \
                 -Dsonar.projectName=DVWA \
                 -Dsonar.login=admin \
                 -Dsonar.password=adminadmin"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: false
            }
        }
    }
}
}
