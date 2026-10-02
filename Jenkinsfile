pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t jenkins-1:latest .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'

                bat '''
                    docker stop jenkins-demo-app || exit /b 0
                    docker rm jenkins-demo-app || exit /b 0
                    docker run -d -p 3000:3000 --name jenkins-demo-app jenkins-1:latest
                '''
            }
        }
    }
}