pipeline {
    agent {
            docker {
                image 'node:18-alpine'
                reuseNode true
            }
    }
    stages {
        stage('Install') {
            steps {
                sh '''
                ls -la
                node --version
                npm --version
                npm ci
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                npm run build
                ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''
                test -f build/index.html
                npm test
                '''
            }
        }
    }
}
