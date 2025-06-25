pipeline {
  agent any

  environment {
    IMAGE_NAME = "springboot-cinema"
  }

  stages {
    stage('拉取代码') {
      steps {
        git credentialsId: 'your-git-id', url: 'https://github.com/your-repo'
      }
    }

    stage('构建后端 JAR') {
      steps {
        sh 'mvn clean package -DskipTests'
      }
    }

    stage('重建镜像并部署') {
      steps {
        script {
          sh 'docker-compose down'
          sh 'docker-compose build --no-cache'
          sh 'docker-compose up -d'
        }
      }
    }
  }

  post {
    success {
      echo "🎉 部署成功！"
    }
    failure {
      echo "❌ 构建或部署失败，请检查日志。"
    }
  }
}
