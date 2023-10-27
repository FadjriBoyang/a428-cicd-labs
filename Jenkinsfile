node {
    def dockerImage = 'node:16-buster-slim'
    def dockerContainer

    try {
        dockerContainer = docker.image(dockerImage).run('-p 3000:3000')
        
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    } finally {
        if (dockerContainer != null) {
            dockerContainer.stop()
        }
    }
}
