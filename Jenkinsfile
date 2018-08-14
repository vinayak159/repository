pipeline {
         agent any
         stages {
                 stage('Code Build') {
                 steps {
                     echo 'Code Build Stage'
                 }
                 }
                 stage('Sonar test') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Deployment') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Hello"
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
              }
}
