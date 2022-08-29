pipeline{
    agent { node{label 'windows-node'}}
   
    stages{
        stage('Git Checkout'){
            steps{
                git 'https://github.com/amantcs/JenkinsAPP2'
            }
        }
        stage('Build'){
            steps{
                bat 'GitVersion.exe /output buildserver /verbosity Quiet'
                bat 'dotnet restore'
                bat "\"${tool 'M3'}" JenkinsAPP.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
                archiveArtifacts artifacts: 'JenkinsAPP/bin/Debug/netcoreapp3.1/*.*', followSymlinks: false
            }
        }
    }
}
