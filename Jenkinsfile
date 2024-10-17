pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
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
         stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-node-app:1.0 .'
            }
        }
    }
}
