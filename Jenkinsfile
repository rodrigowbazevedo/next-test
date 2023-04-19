pipeline {
    agent none

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
            }
        }

        stage('Export') {
            agent {
                dockerfile true
            }
            steps {
                echo 'Exporting..'
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
                sh 'ls -l out'
                archiveArtifacts artifacts: 'out/'
            }
        }
    }
}
