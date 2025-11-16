pipeline {
    agent any
    stages {
        stage('Build JAR') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t java_hello_student:latest .'
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                sh 'sudo docker-compose down || true'
                sh 'sudo docker-compose up -d --build'
            }
        }
    }
}
