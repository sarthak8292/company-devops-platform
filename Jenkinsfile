

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
                echo 'Checking Python environment'

                sh '''
                    python3 --version

                    if ! python3 -m venv --help >/dev/null 2>&1; then
                        echo "Python venv support is missing."
                        echo "Install the OS package for python3-venv."
                        exit 1
                    fi

                    python3 -m venv .venv

                    .venv/bin/python -m pip install --upgrade pip
                    .venv/bin/python -m pip install flask pytest
                '''
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running Python tests'

                sh '''
                    .venv/bin/python -m pytest -v
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Checking Docker'

                sh 'docker --version'

                echo 'Building Docker image'

                sh '''
                    docker build -t company-devops-platform .
                '''
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

