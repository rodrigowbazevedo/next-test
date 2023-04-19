pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:16-alpine'
                }
            }
            steps {
                echo 'Building..'
                sh 'npm install'
                sh 'npm run build'
                sh 'npm run export'
                sh 'ls -l out'
                stash includes: 'out/**/*', name: 'build'
            }
        }

        stage('Teste') {
            agent {
                label 'inbound-agent'
            }
            steps {
                unstash 'build'
                sh 'ls -l'
                sh 'ls -l out'
            }
        }
    }
}
