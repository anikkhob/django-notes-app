@Library('Shared') _
pipeline{
    agent { label 'Jenkins-Agent'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
            clone("https://github.com/anikkhob/django-notes-app.git/","main")
            }
        }
        stage("Code Build"){
            steps{
            dockerbuild("notes-app","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                dockerpush("dockerHubCreds","notes-app","latest")
            }
        }
        stage("Deploy"){
            steps{
                sh "docker-compose up -d"
            }
        }
        
    }
}
