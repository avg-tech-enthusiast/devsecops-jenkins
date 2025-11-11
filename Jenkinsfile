pipeline {
    agent any
    tools {
        kdl 'JDK8'
    }
    stages {
        stage('Test') {
            steps {
                sh 'java -version'
                sh 'chmod +x gradlew'
                sh './gradlew check'
            }
        }
    }
    post {
        always {
            junit 'build/reports/**/*.xml'
        }
    }
}