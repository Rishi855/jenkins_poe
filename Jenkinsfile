pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE_NAME = "rushikesh855/helloworld:latest"
    }

    stages {
        stage('Build and Push Image') {
            steps {
                script {
                    // Build Docker image
                    docker.build("${DOCKER_IMAGE_NAME}", "-f Dockerfile .")

                    // Push image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        docker.image("${DOCKER_IMAGE_NAME}").push()
                    }
                }
            }
        }
        
        stage('Pull and Run Image') {
            steps {
                script {
                    // Pull Docker image on another system
                    docker.image("${DOCKER_IMAGE_NAME}").pull()

                    // Run a new container from the pulled image
                    docker.image("${DOCKER_IMAGE_NAME}").run()
                }
            }
        }
    }
}
