pipeline {
    agent any

    environment {
        GH_REPO = 'https://github.com/ishaaa444/cicdapp.git'
        GH_BRANCH = 'gh-pages'
        GITHUB_TOKEN = credentials('github-token') // <-- Use your Jenkins credential ID here
    }

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
                // Optional: CSS/JS minification can be added here
            }
        }

        stage('Test') {
            steps {
                echo 'Optional: run HTML/CSS linter'
                // Example: bat 'npx htmlhint index.html' if using htmlhint
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying static site to GitHub Pages'

                // Configure Git user
                bat 'git config --global user.email "jenkins@example.com"'
                bat 'git config --global user.name "Jenkins"'

                // Switch to gh-pages branch (creates if not exists)
                bat 'git checkout -B gh-pages'

                // Add all files
                bat 'git add .'

                // Commit changes (ignore if nothing changed)
                bat 'git commit -m "Automated deploy from Jenkins" || echo No changes to commit'

                // Push using the GitHub token
                bat "git push -f https://${GITHUB_TOKEN}@github.com/ishaaa444/cicdapp.git gh-pages"
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully! Site deployed to GitHub Pages.'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
