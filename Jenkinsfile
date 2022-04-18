pipeline {
    agent any
    environment {
        projectName = "dvwa"
    }

stages {
    stage ("SonarQube Scan") {
       steps {
          withEnv(["PATH=/usr/bin:/usr/local/jdk-11.0.2/bin:/opt/sonarqube/sonar-scanner/bin/"]) {
             withSonarQubeEnv(installationName: 'sonarqube') { 
               sh "sonar-scanner \
                 -Dsonar.projectKey=${projectName} \
                 -Dsonar.sources=. \
                 -Dsonar.host.url=${env.SONAR_HOST_URL} \
                 -Dsonar.login=admin \
                 -Dsonar.password=adminadmin \
                 -Dsonar.projectName=${projectName} \
                 -Dsonar.projectVersion=${env.BUILD_ID}"
           }
         }
       }
     }
  }
}
