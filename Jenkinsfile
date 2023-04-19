pipeline {
    agent {
        docker {
            image 'node:16-alpine'
        }
    }

    stages {
        stage('Teste') {
            steps {
                sh 'node --version'
            }
        }
    }
}
