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
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t jenkins-1:latest .'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                    docker stop jenkins-demo-app 2> NUL || exit /b 0
                    docker rm jenkins-demo-app 2> NUL || exit /b 0
                    docker run -d -p 3000:3000 --name jenkins-demo-app jenkins-1:latest
                '''
            }
        }
    }
}