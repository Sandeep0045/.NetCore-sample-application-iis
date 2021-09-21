pipeline {
    agent any
     triggers {
        githubPush()
      }
    stages {
        stage('Restore packages'){
           steps{
               sh 'dotnet restore '
            }
         }        
        stage('Clean'){
           steps{
               sh 'dotnet clean  --configuration Release'
            }
         }
        stage('Build'){
           steps{
               sh 'dotnet build  --configuration Release --no-restore'
            }
         }
        stage('Publish'){
           steps{
               sh 'dotnet publish  hwwebapp.csproj --configuration Release --no-restore'
             }
        }
         
     
    }
}
