pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
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
