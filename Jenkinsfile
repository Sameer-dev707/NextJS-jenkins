pipeline {
    agent any

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
                withCredentials([string(credentialsId: 'VERCEL_TOKEN', variable: 'VERCEL_TOKEN')]) {
                    bat 'cd my-app && npx vercel --prod --yes --token=%VERCEL_TOKEN%'
                }
            }
        }
    }
}