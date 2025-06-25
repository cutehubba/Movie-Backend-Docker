pipeline {
    agent any
    
    stages {
        stage('Build and Run') {
            steps {
                script {
                    // 1. 确保停止旧容器
                    sh 'docker stop movie_backend || true'
                   
                    // 2. 构建并启动新容器
                    sh 'docker compose up -d --build backend'
                    
                    // 3. 查看日志
                    sh 'docker logs -f movie_backend'
                }
            }
        }
    }
}