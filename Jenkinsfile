pipeline {
    agent any

    stages {
        

        stage('Teste') {
            agent {
                label 'jenkins-slave'
            }
            steps {
                // unstash 'build'
                sh 'ls -l'
            }
        }
    }
}
