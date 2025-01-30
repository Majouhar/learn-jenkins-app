pipeline {
    agent any
    stages {
        stage('Install') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
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
    }
}
