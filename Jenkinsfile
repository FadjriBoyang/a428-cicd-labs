node {
    def dockerImage = 'node:16-buster-slim'

    try {
        def nodeImage = docker.image(dockerImage).using('-p 3000:3000')

        nodeImage.inside {
            stage('Build') {
                sh 'npm install'
            }

            stage('Test') {
                sh './jenkins/scripts/test.sh'
            }
        }
    } finally {
    }
}
