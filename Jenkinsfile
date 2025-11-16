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
                sh 'docker build -t java_hello_student:latest .'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                 sh 'docker rm -f $(docker ps -aq) || true'
                 sh 'docker compose down || true'
                 sh 'docker compose up -d --build'
                //sh 'docker run -d -p 8081:8081 java_hello_student'
            }
        }
    }
}
