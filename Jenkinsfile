pipeline {
    agent any

    stages {
        stage('install') {
            steps {
                bat 'npm install'
            }
        }
        stage('build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('deploy') {
            steps {
                withCredentials([string(credentialsId: 'VERCEL_TOKEN', variable: 'VERCEL_TOKEN')]) {
                    bat 'npx vercel --prod --yes --token=%VERCEL_TOKEN%'
                }
            }
        }
    }
}