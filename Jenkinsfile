pipeline {
    agent any

    // Define environment variables
    environment {
        VERSION = "1.0.5"
        NODE_ENV = "development"
    }

    // Define parameters for conditional stages
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
                echo "Building version ${VERSION} in ${NODE_ENV} environment"
            }
        }

        stage('Test') {
            // Conditional execution
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo 'Testing..'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished — this runs after every build.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
