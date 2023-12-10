pipeline {
    agent any
    
    stages {
        stage('Build and Push Image') {
            steps {
                script {
                    // Build Docker image
                    docker.build("your-dockerhub-username/helloworld:latest")

                    // Push image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                        docker.image("your-dockerhub-username/helloworld:latest").push()
                    }
                }
            }
        }
        
        stage('Pull and Run Image') {
            steps {
                script {
                    // Pull Docker image on another system
                    docker.image("your-dockerhub-username/helloworld:latest").pull()

                    // Run a new container from the pulled image
                    docker.image("your-dockerhub-username/helloworld:latest").run()
                }
            }
        }
    }
}
