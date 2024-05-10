pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // 使用 Maven 运行测试，并生成 Surefire 报告
                bat 'mvn clean test'
                archiveArtifacts artifacts: 'target/surefire-reports/*.xml', fingerprint: true
            }
        }
        stage('Generate Javadoc') {
            steps {
                // 使用 Maven 生成项目的 Javadoc
                bat 'mvn javadoc:jar'
                archiveArtifacts artifacts: 'target/site/apidocs/**', fingerprint: true
            }
        }
    }
    
    post {
        always {
            // 清理构建产物
            cleanWs()
        }
    }
}
