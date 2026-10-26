

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code checked out from GitHub'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat '"C:\\Users\\SARTHAK\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" --version'
                bat '"C:\\Users\\SARTHAK\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pip install flask pytest'
            }
        }

        stage('Run Tests') {
            steps {
                bat '"C:\\Users\\SARTHAK\\AppData\\Local\\Programs\\Python\\Python314\\python.exe" -m pytest -v'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '"C:\\Users\\SARTHAK\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" --version'
                bat '"C:\\Users\\SARTHAK\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" build -t company-devops-platform .'
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
    }
}
