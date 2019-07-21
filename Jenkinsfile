pipeline {
    agent any
    
    stages {
        stage ('Checkout') {
          steps {
            git 'https://github.com/sbabburu/jenkins-pipelines.git'
          }
        }
        stage('Build') {
            tools
            {
                docker 'latest'
            }   
            agent { docker 'maven:3.5-alpine' }
            steps {
                sh 'mvn clean package'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    
    }
}
