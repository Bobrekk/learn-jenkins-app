pipeline {
    agent any

    stages {
        agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
        stage('Build') {
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh ''' 
                    npm ci
                    npm run build
                    test -f public/index.html
                    npm test
                '''
            }
        }
    }
}