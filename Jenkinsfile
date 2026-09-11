pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Test Coverage') {
            steps {
                bat 'npm run coverage'
            }
        }

        stage('Security Audit') {
            steps {
                bat 'npm audit'
            }
        }
    }
}
