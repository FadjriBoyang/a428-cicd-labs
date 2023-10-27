node {
    docker {
        image 'node:16-buster-slim'
        args '-p 3000:3000'
    }

    sh 'npm install && ./jenkins/scripts/test.sh'
}
