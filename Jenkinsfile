pipeline {
    agent any
    tools {
        jdk 'JDK8'
    }
    stages {
        stage('Build') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew build --no-daemon'
            }
        }
        stage('Test') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew test --no-daemon'
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            // Only try to archive test results if the file exists
            dir('build/test-results/test') {
                if (fileExists('TEST-*.xml')) {
                    junit 'build/test-results/test/*.xml'
                }
            }
        }
    }
}
