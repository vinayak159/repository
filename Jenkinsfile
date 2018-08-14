pipeline {
         agent any
         stages {
                 stage('Pull Code from Git') {
                 steps {
                     echo 'Code Build Stage'
                 }
                 }
                 stage('Sonar test') {
                 steps {
                    input('Do you want to proceed?')
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
