node {
    checkout scm

    docker.image('maven:3.9.4-eclipse-temurin-17-alpine').inside('-v /root/.m2:/root/.m2') {
        stage('Build') {
            sh 'mvn -B -DskipTests clean package'
        }
        stage('Test') {
            sh 'mvn test'
            junit 'target/surefire-reports/*.xml'
        }
        stage('Manual Approval') {
			input message: 'Lanjutkan ke tahap Deploy? (klik Proceed untuk melanjutkan atau Abort untuk menghentikan)'
        }
        stage('Deploy') {
			sh './jenkins/scripts/deliver.sh'
            sleep time: 1, unit: 'MINUTES'
        }
    }
}