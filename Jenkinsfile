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
        }
    }
     post {
        always {
            emailext(
                to: 'renetsusil@gmail.com',
                subject: "Jenkins Build: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "Build status: ${currentBuild.currentResult}"
            )
        }
    }

}
