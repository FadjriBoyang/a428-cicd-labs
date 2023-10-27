node {
    try {
        def dockerImage = docker.image('node:16-buster-slim')
        def dockerContainer = dockerImage.run('-p 3000:3000')
        
        stage('Build') {
            steps {
                script {
                    dockerContainer.inside {
                        sh 'npm install'
                    }
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    dockerContainer.inside {
                        sh './jenkins/scripts/test.sh'
                    }
                }
            }
        }
    } finally {
        dockerContainer.stop()
    }
}
