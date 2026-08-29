pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('VERCEL_TOKEN')
    }

    stages {
        stage('install') {
            steps {
                bat 'cd my-app && npm install'
            }
        }
        stage('build') {
            steps {
                bat 'cd my-app && npm run build'
            }
        }
        stage('deploy') {
            steps {
                bat 'cd my-app && npx vercel --prod --yes --token=%VERCEL_TOKEN%'
            }
        }
    }
}