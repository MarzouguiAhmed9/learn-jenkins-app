pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                echo "hani njareb"
                pwd
                ls -al  # Check workspace
                npm ci
                npm run build
                '''
            }
        }

        stage('test') {
            steps {
                echo "test stages"
            }
        }
    }
}

