pipeline {
    agent any
    tools {
         maven 'maven 3.3.3'
    }
    stages {
        stage ('Checkout') {
          steps {
            git 'https://github.com/sbabburu/jenkins-pipelines.git'
          }
        }
        stage('Build') {
              
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    
    }
}
