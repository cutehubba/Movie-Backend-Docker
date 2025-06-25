pipeline {
    agent any
    
    stages {
        stage('Hello') {
            steps {
                echo '✅ 这个步骤永远不会失败'
                sh 'echo "这是一个简单的Shell命令"'
                sh 'ls -l'  // 列出当前目录文件（总是成功）
            }
        }
        
        stage('Generate Artifact') {
            steps {
                // 创建一个简单的文件作为"构建产物"
                sh '''
                    echo "构建时间: $(date)" > build-info.txt
                    echo "构建ID: ${BUILD_ID}" >> build-info.txt
                '''
                
              
            }
        }
    }
    
    post {
        always {
            echo '🎉 流水线执行完成（无论成功与否都会显示）'
        }
    }
}