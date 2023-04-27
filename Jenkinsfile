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
                echo $BUILD_NUMBER
                sh 'npm install'
                sh 'npm run build'
                stash includes: 'out/**/*', name: 'build'
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

        // stage('Publish') {
        //     agent {
        //         label 'inbound-agent'
        //     }
        //     steps {
        //         unstash 'build'
        //         sh 'ls -l out'
        //         archiveArtifacts artifacts: 'out/'
        //     }
        // }
    }
}
