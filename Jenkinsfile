


@Library('jenkins_shared_library') _
pipeline {
    agent any 
    
    environment {
        GIT_CREDENTIALS = 'github_cred' 
    }

    tools {
        maven 'maven'  
    }
      stages{
        stage('Git checkout code'){
            steps{
                echo 'Checking out code from Git...'
                script{
                gitCheckout(
                  branch: "main" ,
                  url: "https://github.com/kasireddysairam/java_app_01.git" ,
                  credentialsId: env.GIT_CREDENTIALS
                 
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
