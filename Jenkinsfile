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
                npm ci
                npm run build
                ls -al build/
                '''
            }
        }

        stage('test') {  // Renamed second 'build' to avoid name conflict
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh ''' 
                 if [ -f build/index.html ]; then
                   echo "Build folder exists and contains index.html"
                 else
                   echo "Build folder or index.html is missing!"
                 fi
                 npm test
                 '''
            }
        }
    
        stage('bdeploy') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                sh '''
                npm install netlify-cli -g
                '''
            }
        }
    }

    post {
        always {
            sh 'ls -al build/ || echo "Build folder not found"'
        }
    }
}
