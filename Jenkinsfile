pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Static site - no build required'
            }
        }

        stage('Test') {
            steps {
                echo 'Optional: run HTML/CSS linter'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying static site'
                // Copy files to a deploy folder (local example)
                bat 'mkdir deploy'
                bat 'xcopy /E /Y /I index.html deploy\\'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
