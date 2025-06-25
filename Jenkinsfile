pipeline {
    agent any

    stages {
        stage('Build Java Application') {
            steps {
                script {
                    echo '开始清理并打包 Spring Boot 应用程序...'
                    bat 'mvn clean package -DskipTests'
                    echo 'Maven 打包完成，已生成 JAR 文件。'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    echo '开始构建 Docker 镜像...'
                    def dockerImage = "movie-backend:${env.BUILD_NUMBER}"
                    bat "docker build -t ${dockerImage} ."
                    echo "Docker 镜像 ${dockerImage} 构建成功。"
                }
            }
        }
    }

    post {
        always {
            echo '流水线执行完毕，开始归档和清理...'
            archiveArtifacts artifacts: 'target/*.jar', allowEmptyArchive: false
            echo '已归档 JAR 文件。'
            archiveArtifacts artifacts: 'backend.log', allowEmptyArchive: true
            echo '已归档 backend.log (如果存在)。'
        }
        failure {
            echo '流水线执行失败。请检查日志获取详细信息。'
        }
        success {
            echo '流水线执行成功。'
        }
    }
}