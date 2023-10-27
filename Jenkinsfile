node {
    try {
    docker.image('node:16-buster-slim').withRun('-p 3000:3000') {
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
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the website? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
    }catch (Exception e) {
        currentBuild.result = 'FAILURE'
        throw e
    }
}


