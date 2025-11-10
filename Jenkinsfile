pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
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