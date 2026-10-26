
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checked out from GitHub'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing Python dependencies'
                sh 'python3 --version'
                sh 'python3 -m pip install --user flask pytest'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Python tests'
                sh 'python3 -m pytest -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image'
                sh 'docker --version'
                sh 'docker build -t company-devops-platform .'
            }
        }
    }

    post {
        success {
            echo 'CI Pipeline completed successfully!'
        }
        failure {
            echo 'CI Pipeline failed. Please check the console output.'
        }
        always {
            echo 'Jenkins pipeline execution finished.'
        }
    }
}

