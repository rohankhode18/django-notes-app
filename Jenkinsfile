@Library("shared-libraries") _

pipeline {
    agent { label "mike" }
    
    stages {

        stage("Code"){
            steps{
              script{
                  clone("https://github.com/rohankhode18/django-notes-app.git","main")
              }
            }
        }

        stage("Build") {
            steps {
                script{
                    docker_build("django-notes-app","latest","rohankhode")    
                }
            }
        }

        stage("Pushing image") {
            steps {
                script{
                    echo "Pushing Image to Docker Hub"
                    docker_push("django-notes-app","latest","rohankhode")
                }
            }
        }


        stage("Deploy") {
            steps {
                script{
                echo "Deploying with Docker Compose"
                    docker_deploy()
                }
                
            }
        }
    }
}
