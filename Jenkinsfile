pipeline {
   
   agent {
       dockerfile true
      
   }
    stages {
       stage('JUnit Test') {
            steps {
                sh 'mvn clean'
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
