pipeline {
    agent any

    stages {
        // 1. Checkout Stage (CI)
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Mdzaidsiddique/Jenkins-CI-CD-Implementation.git'
            }
        }

        // 2. Build Stage (CI)
        stage('Build') {
            steps {
                script {
                    echo "building .."
                }
            }
        }

        // 3. Test Stage (CI)
        stage('Test') {
            steps {
                script {
                    echo "testing.."
                }
            }
        }

        // 4. Deploy Stage (CD)
        stage('Deploy') {
            steps {
                script {
                    echo "deploying.."
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
        success {
            echo 'Build and deployment were successful!'
        }
        failure {
            echo 'Build or deployment failed.'
        }
    }
}
