pipeline {
    agent any 

    environment {
        VERCEL_TOKEN = credentials('vercel_token')
    }

    stages {
        stage('install') {
            steps {
                bat 'npm install'
            }
        }
        stage('test') {
            steps {
                echo 'skipping test'
            }
        }
        stage('build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('deploy') {
            steps {
                bat 'npx vercel --prod --name=nextjs-jenkins --yes --token=%VERCEL_TOKEN%'
            }
        }
    }
}
