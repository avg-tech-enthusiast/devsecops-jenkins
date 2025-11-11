pipeline {
    agent any
    stages {
        stage('No-op') {
            steps {
                sh 'ls'
            }
        }
    }
    post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            mail to: 'hugo.lisiecki@edu.devinci.fr',
                 subject: "Succesful Pipeline: ${currentBuild.fullDisplayName}",
                 body: "${env.BUILD_URL} is working smh"
        }
        unstable {
            mail to: 'hugo.lisiecki@edu.devinci.fr',
                 subject: "Unstable Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is weird with ${env.BUILD_URL}"
        }
        failure {
            mail to: 'hugo.lisiecki@edu.devinci.fr',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
        changed {
            mail to: 'hugo.lisiecki@edu.devinci.fr',
                 subject: "Changed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something chnaged with ${env.BUILD_URL}"
        }
    }
}