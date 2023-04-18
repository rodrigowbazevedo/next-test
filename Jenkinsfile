pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                label 'node-agent'
            }
            steps{
                echo 'Building..'
                sh 'node --version'
                sh 'npm install'
                sh 'npm run build'
                sh 'npm run export'
                sh 'ls -l out'
            }
        }

        stage('Teste') {
            agent {
                label 'inbound-agent'
            }
            steps{
                sh 'pwd'
                sh 'ls -l'
            }
        }
    }
}
