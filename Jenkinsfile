pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Pulling latest code from SCM...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Static site - no build required'
                // Optional: add CSS/JS minification or pre-processing here
            }
        }

        stage('Test') {
            steps {
                echo 'Optional: run HTML/CSS linter'
                // Example: bat 'npx htmlhint index.html' if you have htmlhint installed
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying static site'

                // Option 1: Copy to a local deploy folder
                bat 'mkdir deploy'
                bat 'xcopy /E /Y /I * deploy\\'

                // Option 2 (Advanced): Automatically push to GitHub Pages
                // Uncomment if you want to push to gh-pages branch
                /*
                bat 'git config --global user.email "jenkins@example.com"'
                bat 'git config --global user.name "Jenkins"'
                bat 'git checkout -B gh-pages'
                bat 'git add .'
                bat 'git commit -m "Automated deploy from Jenkins" || echo "No changes to commit"'
                bat 'git push -f https://<TOKEN>@github.com/ishaaa444/cicdapp.git gh-pages'
                */
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
