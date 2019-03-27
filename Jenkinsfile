pipeline {
   agent {
       dockerfile true
   }
   stages {

         stage('Checkout Code') { 
            git 'https://github.com/maping/java-maven-calculator-web-app.git'
         }
         stage('JUnit Test') {

            sh "mvn clean test"

         }
         stage('Integration Test') {

            sh "mvn integration-test"

         }
       /*
         stage('Performance Test') {
            if (isUnix()) {
               sh "'${mvnHome}/bin/mvn' cargo:start verify cargo:stop"
            } else {
               bat(/"${mvnHome}\bin\mvn" cargo:start verify cargo:stop/)
            }
         }
        */
        stage('Performance Test') {

           sh "mvn verify"

         }
         stage('Deploy') {
            timeout(time: 10, unit: 'MINUTES') {
                 input message: 'Deploy this web app to production ?'
            }
            echo 'Deploy...'
         }

         stage('Build') {
            sh 'docker build -t calculator .'
         }
   }
}
   
