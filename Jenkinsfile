pipeline {
    agent any
    
    stages {
        stage('Run Backend') {
            steps {
                // 1. 拉取代码
                checkout scm
                
                // 2. 直接运行Spring Boot应用 (阻塞式)
                sh 'mvn spring-boot:run'
                
                // 或者后台运行 (非阻塞式，可选)
                // sh 'nohup mvn spring-boot:run > backend.log 2>&1 &'
                // sleep 30  // 等待启动
            }
        }
    }
}