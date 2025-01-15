pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                Docker{
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
                    npm build 
                    ls -la
                '''
                
            }
        }
    }

    stages{
        step{
            sh 'test -f build/index.html'
        }
    }
}
