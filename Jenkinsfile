node {
    docker {
        image 'node:16-buster-slim'
        args '-p 3000:3000'
    }

    stage('build'){
        sh 'npm install'
    }
    stage('test') {
         sh './jenkins/scripts/test.sh'
    }
}
