pipeline {
    agent any

    environment {
        GITHUB_TOKEN = credentials('jenkins-cicd')
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Vikrant657/portfolio.git', branch: 'main'
            }
        }

        stage('Build and Deploy to GitHub Pages') {
            steps {
                sh 'git config --global user.email "vikrant6578@gmail.com"'
                sh 'git config --global user.name "vikrant"'

                sh '''
                    git checkout -b gh-pages
                    git add .
                    git commit -m "Auto-deploy via Jenkins"
                    git push -f https://${GITHUB_TOKEN}@github.com/vikrant657/portfolio.git gh-pages
                '''
            }
        }
    }

    post {
        success {
            echo ' Deployment successful!'
        }
        failure {
            echo ' Deployment failed!'
        }
    }
}
