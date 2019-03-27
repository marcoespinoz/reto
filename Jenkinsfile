pipeline {
   def mvnHome = tool 'M3'
   agent {
       dockerfile true
   }
    stages {
       stage('JUnit Test') {
            steps {
                sh 'mvn clean test'
            }
        }
        stage('Integration Test') {
            steps {
                sh 'mvn integration-test'
            }
        }
       stage('Deploy') {
            steps {
                sh 'mvn install'
            }
        }
    }
}
