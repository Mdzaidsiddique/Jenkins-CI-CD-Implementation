pipeline {
    agent any  // Runs on any available Jenkins agent

    environment {
        // Define environment variables, if necessary
        NODE_ENV = 'production'
    }

    stages {
        // 1. Checkout Stage (CI)
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-repo.git'
            }
        }

        // 2. Build Stage (CI)
        stage('Build') {
            steps {
                script {
                    // Define your build process here (e.g., npm install, maven build)
                    sh 'npm install'
                }
            }
        }

        // 3. Test Stage (CI)
        stage('Test') {
            steps {
                script {
                    // Run tests to ensure quality (e.g., unit tests, integration tests)
                    sh 'npm test'
                }
            }
        }

        // 4. Deploy Stage (CD)
        stage('Deploy') {
            steps {
                script {
                    // Deploy to a server, Kubernetes, or a cloud service (e.g., Docker container, SSH to server)
                    sh 'npm run deploy'
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()  // Cleans up the workspace
        }
        success {
            echo 'Build and deployment were successful!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}
