pipeline {
    agent any
    stages {
        stage('Build with Docker') {
            steps {
                sh 'docker compose down'
                sh 'docker compose up -d --build backend'
            }
        }
    }
}