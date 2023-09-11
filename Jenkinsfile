node {
    checkout scm

    docker.image('maven:3.9.4-eclipse-temurin-17-alpine') {
        stage('Build') {
            sh 'mvn -B -DskipTests clean package'
        }
        stage('Test') {
            sh 'mvn test'
            junit 'target/surefire-reports/*.xml'
        }
    }
}