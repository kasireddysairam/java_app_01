


@Library('jenkins_shared_library') _
pipeline {
    agent any 
    parameters {
        choice(name: 'action',choices: 'create\ndelete', description:'choose create/destroy')
         string(name: 'ImageName', description: "name of the docker build", defaultValue: 'javapp')
        string(name: 'ImageTag', description: "tag of the docker build", defaultValue: 'v1')
        string(name: 'DockerHubUser', description: "name of the Application", defaultValue: 'sairamk1998')

        
    }
      stages{
        stage('Git checkout code'){
            when { expression { params.action == 'create'}}
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
             when { expression { params.action == 'create'}}
            steps{
               script{
                   mvnTest()
               }
            }
        }
    stage('Integration Test maven'){
         when { expression { params.action == 'create'}}
            steps{
               script{
                   mvnIntegrationTest()
               }
            }
        }
       stage('Quality gate Analysis SonarQube'){
            when { expression { params.action == 'create'}}
            steps{
               script{
                   def sonarqubecred = 'sonarqube_credt' 
                 staticcodeAnalysis(sonarqubecred)
            }
        }
       }

          stage('Quality Gate Status Check : Sonarqube'){
         when { expression {  params.action == 'create' } }
            steps{
               script{
                   
                   def SonarQubecredentialsId = 'sonarqube_credt'
                   QualityGateStatus(SonarQubecredentialsId)
               }
            }
        }

         stage('Maven Build : maven'){
         when { expression {  params.action == 'create' } }
            steps{
               script{
                   mvnBuild()
               }
            }
        }
     stage('Docker Image Build'){
         when { expression {  params.action == 'create' } }
            steps{
               script{
                
                   dockerBuild("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
               }
            }
        }
    



          

      }
}
