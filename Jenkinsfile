@Library("Shared") _
pipeline {
    
    agent { label "vinod"}

    stages {
        stage("Hello"){
            steps{
                  hello()
              }
            }
        stage("Code") {
            steps {
                clone("https://github.com/bhushanpatil251/django-notes-app", "main")
                echo "Code cloned successfully"
            }
        }
        stage("Build and Test") {
            steps {
                docker_build("django-app","latest","bhushanpatil")
                echo "Code Build successfully"
            }
        }
        stage("Push To DockerHub"){
            steps{
                docker_push("django-app","latest","bhushanpatil")
                }
            }
        stage("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d --build"
            }
        }
    }
}
