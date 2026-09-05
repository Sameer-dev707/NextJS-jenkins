node {
    def appDir = '/var/www/nextjs-app'

    stage('clean workspace') {
        echo 'cleaning jenkins workspace'
        deleteDir()
    }

    stage('clone repo') {
        echo 'cloning the repo'
        git(
            branch: 'main',
            url: 'https://github.com/Sameer-dev707/NextJS-jenkins')
    }

    stage('deploy to EC2') {
        echo 'deploying to EC2'
        sh """
           sudo mkdir -p ${appDir}
           sudo chown -R jenkins:jenkins ${appDir}
           rsync -av --delete --exclude='.git' --exclude='node_modules' ./ ${appDir}
           cd ${appDir}
           sudo npm install
           sudo npm run build
           sudo fuser -k 3000/tcp || true
           npm run start
          """
    }
}