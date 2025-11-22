@Library('Shared') _
pipeline {
    agent { label 'Jenkins-Agent' }

    stages {

        stage("Code clone") {
            steps {
                sh "whoami"
                script {
                    clone("https://github.com/anikkhob/django-notes-app.git", "main")
                }
            }
        }

        stage("Code Build") {
            steps {
                script {
                    docker_build("notes-app", "latest")
                }
            }
        }

        stage("Push to DockerHub") {
            steps {
                script {
                    docker_push("dockerHubCreds", "notes-app", "latest")
                }
            }
        }

        stage("Deploy") {
            steps {
                sh "docker-compose up -d"
            }
        }
    }
}
