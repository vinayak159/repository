pipeline {
         agent any
         stages {
                 stage('Pull Code from Git') {
                 steps {
                     echo 'Code Build Stage'
                 }
                 }
                 stage('SonarQube Analysis') {
                 steps {
                    input('Do you want to proceed?')
                    withSonarQubeEnv('Sonar') {
                    // requires SonarQube Scanner for Maven 3.2+
                    sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
                           }
                      }         
                 }
                 stage('Dev Deployment') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Dev Deployment Successful!!"
                 }
                 }
                 stage('Testing') {
                 parallel { 
                            stage('Unit Test') {
                           steps {
                                echo "Running the unit test..."
                           }
                           }
                            stage('Integration test') {

                              steps {
                                echo "Running the integration test..."
                              }
                           }
                           }
                           }
                 stage('Prod Deployment') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Production Deployment Successful!!"
                 }
                 }
              }
}
