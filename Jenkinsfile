pipeline {
    agent any

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
                echo 'Building..'
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
