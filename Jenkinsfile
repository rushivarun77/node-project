pipeline {
    agent any 
    stages{
        stage("checkout"){
            steps{
                 checkout scm
            }
        }
        stage("Test") {
            steps {
                // Install Node.js (if not already installed) using Chocolatey package manager
                bat '''
                choco install nodejs -y
                npm install
                '''

                // Run npm tests
                bat 'npm test'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Build your Docker image
                    bat 'docker build -t my-nodejs-app .'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    // Deploy your Docker image
                    echo 'Deploying application...'
                }
            }
        }
    }
}
