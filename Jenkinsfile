pipeline {
    agent any
    
    parameters {
        string(name: 'BRANCH', description: 'Branch to build', defaultValue: 'main')
        booleanParam(name: 'RUN_TESTS', description: 'Run tests?', defaultValue: true)
    }
    
    environment {
        CUSTOM_ENV_VARIABLE = 'CustomValue'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Clone the repository
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building branch ${params.BRANCH}"
            }
        }
        
        stage('Test') {
            when {
                expression { params.RUN_TESTS }
            }
            steps {
                echo "Running tests..."
            }
        }
        
        stage('Deploy') {
            steps {
                echo "Deploying..."
                echo "Custom environment variable: ${CUSTOM_ENV_VARIABLE}"
            }
        }
    }
}
