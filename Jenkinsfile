node {
    try {
        def dockerImage = docker.image('node:16-buster-slim')
        def dockerContainer

        // Start the Docker container and assign it to the dockerContainer variable
        dockerContainer = dockerImage.run('-p 3000:3000')

        stage('Build') {
            steps {
                script {
                    // Run npm install inside the Docker container
                    dockerContainer.inside {
                        sh 'npm install'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run test.sh inside the Docker container
                    dockerContainer.inside {
                        sh './jenkins/scripts/test.sh'
                    }
                }
            }
        }
    } finally {
        // Clean up the Docker container
        if (dockerContainer != null) {
            dockerContainer.stop()
        }
    }
}
