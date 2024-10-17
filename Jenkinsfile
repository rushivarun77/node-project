pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'choco install nodejs -y || echo "Chocolatey already installed"'
                bat 'node -v'
                bat 'npm -v'
            }
        }
        stage('Test') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build') {
            steps {
                echo 'Build process...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}
