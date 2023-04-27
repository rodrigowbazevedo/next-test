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
                echo "${GIT_COMMIT}"
                echo "${BUILD_NUMBER}"
                sh 'npm install'
                sh 'npm run build'
                sh 'npm run export'
                sh 'ls -l out'
                stash includes: 'out/**/*', name: 'build'
            }
        }

        stage('Publish') {
            agent {
                dockerfile true
            }
            steps {
                unstash 'build'
                sh 'ls -l out'
                archiveArtifacts artifacts: 'out/'
            }
        }
    }
}
