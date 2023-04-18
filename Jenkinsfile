pipeline {
    agent any

    stages {
        stage('Prepare') {
            steps{
                script{
                    env.git_url = 'https://github.com/rodrigowbazevedo/next-test.git'
                    env.app_name = 'next-teste'
                }
            }
        }

        stage('Build') {
            steps{
                echo 'Building..'
                sh 'sleep 20'
                sh 'node --version'
                sh 'ls -l'
            }
        }
    }
}
