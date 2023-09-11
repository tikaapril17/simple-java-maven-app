node {
    try {
        // Set agent to run on a Docker container
        def mydocker = docker.image('node:16-buster-slim').run('-p 49000:49000')

        // Define the stages
        stage('Build') {
            // Inside the Build stage
            node(mydocker) {
                // Run npm install
                sh 'npm install'
            }
        }

        stage('Test') {
            // Inside the Test stage
            node(mydocker) {
                // Run the test.sh script
                sh './jenkins/scripts/test.sh'
            }
        }
    } finally {
        // Clean up the Docker container
        mydocker.stop()
    }
}
