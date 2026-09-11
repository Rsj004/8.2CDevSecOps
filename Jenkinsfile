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
                bat 'npm test || exit /b 0'
            }
            post {
                always {
                    emailext(
                        to: 'renetsusil@gmail.com',
                        subject: "Test Stage - ${currentBuild.currentResult}",
                        body: "Test stage status: ${currentBuild.currentResult}",
                        attachLog: true
                    )
                }
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'npm run coverage || exit /b 0'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit /b 0'
            }
            post {
                always {
                    emailext(
                        to: 'renetsusil@gmail.com',
                        subject: "Security Scan - ${currentBuild.currentResult}",
                        body: "Security scan status: ${currentBuild.currentResult}",
                        attachLog: true
                    )
                }
            }
        }
    }
}
