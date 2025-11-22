pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    environment {
        VERSION = '1.0.0'
    }

    // Parameters (added as requested)
    parameters {
        booleanParam(
            name: 'executeTests',
            defaultValue: true,
            description: 'Run the Test stage?'
        )
    }

    stages {
        stage('Build') {
            steps {
                echo "Building version ${VERSION}"
                bat 'mvn -version'
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo "Running Tests because executeTests = true"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying..."
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
