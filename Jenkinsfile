pipeline {
    agent any 
    stages{
        stage("checkout"){
            steps{
                 checkout scm
            }
        }
       steps {
                // Install Node.js using Chocolatey and run npm commands
                bat '''
                @echo off
                REM Check if Chocolatey is installed
                choco -v || (
                    echo "Installing Chocolatey..." 
                    powershell -Command "Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
                )

                REM Install Node.js
                choco install nodejs -y || echo "Node.js is already installed."

                REM Verify Node.js and npm installation
                node -v || (echo "Error: Node.js installation failed." & exit /b 1)
                npm -v || (echo "Error: npm is not recognized." & exit /b 1)

                REM Install npm packages
                echo "Running npm install..."
                npm install || (echo "npm install failed." & exit /b 1)

                REM Run npm tests
                echo "Running npm test..."
                npm test || (echo "npm test failed." & exit /b 1)
                '''
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
