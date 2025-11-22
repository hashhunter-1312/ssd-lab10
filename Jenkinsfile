pipeline {
    agent any

    // Build tools (Maven)
    tools {
        maven 'Maven'
    }

    // Environment variables
    environment {
        VERSION = '1.0.0'
    }

    stages {

        stage('Build') {
            steps {
                echo "Building version ${VERSION}"
                bat 'mvn -version'      // Required for Windows
            }
        }

        stage('Test') {
            steps {
                echo "Testing version ${VERSION}"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${VERSION}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline Completed'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
