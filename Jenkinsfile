


@Library('jenkins_shared_library') _
pipeline {
    agent any 
    parameters {
        choice(name: 'action',choices: 'create\ndelete', description:'choose create/destroy')
    }
      stages{
          when { expression { param.action == 'create'}}
        stage('Git checkout code'){
            steps{
                echo 'Checking out code from Git...'
                script{
                gitCheckout(
                  branch: "main" ,
                  url: "https://github.com/kasireddysairam/java_app_01.git" )
                }
            }
        }
        stage('Unit Test maven'){
            when { expression { param.action == 'create'}}
            steps{
               script{
                   mvnTest()
               }
            }
        }
    stage('Integration Test maven'){
        when { expression { param.action == 'create'}}
            steps{
               script{
                   mvnIntegrationTest()
               }
            }
        }
       stage('Quality gate Analysis SonarQube'){
        when { expression { param.action == 'create'}}
            steps{
               script{
                  vars/staticcodeAnalysis()
            }
        }


          
            
    

      }
}
