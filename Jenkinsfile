node {
    docker.image('node:16-buster-slim').withRun('-p 49000:49000') {
        stage('Build') {
        sh 'npm install'
        }

        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
    }       
}