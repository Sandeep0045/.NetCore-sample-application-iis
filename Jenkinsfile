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
        
        stage('Push') {
            steps {
              sh """
              cd ${WORKSPACE}/bin/Deubg
              /bin/zip -r net5_0.zip net5.0/
              /bin/jfrog rt u net5_0.zip  dotnetcore/  --url http://34.141.137.211:8082/artifactory --user admin --password Emids9211!
               """
}
}
         
     
    }
}
