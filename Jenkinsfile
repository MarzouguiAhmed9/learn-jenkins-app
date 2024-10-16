pipeline {
    agent any

    stages {
        stage('sans docker') {
            steps {
                sh 'echo "hello  world"'
                sh 'touch sanscon.txt'
            }
        }
        
        stage('avec docker'){
            agent { docker { image 'node:18-alpine'
                                reuseNode true                 } }
            
            steps {
                sh 'echo "hello docker world"'
                sh 'touch aveccont.txt'
            }
        }
    }
}
