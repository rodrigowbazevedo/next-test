pipeline {
    agent {
        docker { image 'node:16' }
    }

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
                sh 'node --version'
                sh 'ls -l'
            }
        }
    }
}
