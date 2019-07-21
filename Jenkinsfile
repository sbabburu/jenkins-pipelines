pipeline {
    agent any
    
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
