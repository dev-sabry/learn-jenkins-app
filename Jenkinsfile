pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    npm config set loglevel=silly
                    npm config set fetch-retries 5
                    npm config set fetch-retry-factor 10
                    npm config set fetch-retry-maxtimeout 1200000
                    npm config set fetch-retry-mintimeout 600000
                    npm config set fetch-timeout 1800000
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
    }
}
