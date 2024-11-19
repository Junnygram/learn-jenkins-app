pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                sh 'echo "Hello world "'
                sh 'whoami'
            }
        }
      
        stage('Build Docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Hello from docker agent"
                    ls -la
                    npm --version
                    node --version
                    npm ci
                    npm run build
                    touch container.yes.txt
                '''
            }
        }
    }
}
