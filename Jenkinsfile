pipeline {
    agent any 

      stages{
        stage('Git checkout code'){
            steps{
                 echo 'Checking out code from Git...'
                script{
                 git branch: 'main', credentialsId: 'github_cred', url: 'https://github.com/kasireddysairam/java_app_01.git'

                }
            }
        }



      }
}