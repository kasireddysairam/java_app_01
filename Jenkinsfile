


@Library('jenkins_shared_library') _
pipeline {
    agent any 
    
   
   
      stages{
        stage('Git checkout code'){
            steps{
                echo 'Checking out code from Git...'
                script{
                gitCheckout(
                  branch: "main" ,
                  url: "https://github.com/kasireddysairam/java_app_01.git" ,
                 
                 
                )

                }
            }
        }
        stage('Unit Test maven'){
            steps{
               script{
                   maventest()
               }
            }
        }




      }
}
