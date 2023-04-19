pipeline {
    agent {
        label 'jenkins-slave'
    }

    stages {
        stage('Teste') {
            steps {
                // unstash 'build'
                sh 'ls -l'
            }
        }
    }
}
