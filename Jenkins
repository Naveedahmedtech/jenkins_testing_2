pipeline {
    agent any
    environment {
        GITHUB_TOKEN = credentials('github-pat-token-1')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build and Test') {
            steps {
                bat 'npm install'
                bat 'npm test'
            }
        }
    }
    post {
        success {
            script {
                echo "Build succeeded. GitHub token is available."
            }
        }
        failure {
            echo "Build failed. Notifying GitHub..."
        }
    }
}
