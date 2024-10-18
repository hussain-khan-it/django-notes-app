@Library("Shared") _
pipeline{
    
    agent { label "node-a"}
    
    stages{
        
        stage("Code Clone"){
            steps{
               script{
                clone("https://github.com/hussain-khan-it/django-notes-app.git","main")
               }
                
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest-18oct","hussainkhanmcs")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest-18oct","hussainkhanmcs")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
