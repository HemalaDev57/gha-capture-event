pipeline {
    agent any  // Runs on any available agent

    environment {
        // Set environment variables here
        // Example:
        // MY_VAR = 'value'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // This will check out the current branch
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run the build commands for your project (e.g., for Go, Node.js, Java)
                    echo "Building the project..."
                    sh 'make build'  // Change this based on your build tool or language
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run your tests here
                    echo "Running tests..."
                    sh 'make test'  // Adjust this to your test commands
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'  // Deploy only from the main branch (can be adjusted)
            }
            steps {
                script {
                    // Deploy your application
                    echo "Deploying to production..."
                    sh './deploy.sh'  // Replace with your deploy script/command
                }
            }
        }

        stage('Post-Deployment') {
            when {
                branch 'main'  // This will run only for the main branch
            }
            steps {
                script {
                    // Any post-deployment activities (e.g., sending notifications)
                    echo "Running post-deployment tasks..."
                    // Example:
                    // sh './post-deployment-script.sh'
                }
            }
        }
    }

    post {
        always {
            // Runs after every pipeline execution, regardless of success/failure
            echo 'Cleaning up...'
        }

        success {
            // Runs only if the pipeline is successful
            echo 'Pipeline executed successfully.'
        }

        failure {
            // Runs only if the pipeline fails
            echo 'Pipeline failed!'
        }
    }
}
