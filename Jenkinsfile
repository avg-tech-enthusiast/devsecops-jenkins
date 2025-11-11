pipeline {
    agent any
    tools {
        jdk 'JDK8'
    }
    stages {
        stage('Check Environment') {
            steps {
                sh 'echo $JAVA_OPTS'
                sh 'echo $GRADLE_OPTS'
            }
        }
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