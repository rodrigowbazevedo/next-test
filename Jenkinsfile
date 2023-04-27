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
                echo $GIT_COMMIT
                script {
                    def build = currentBuild

                    def commitHash = build?.actions.find { action -> action instanceof jenkins.scm.api.SCMRevisionAction }?.revision?.hash

                    echo "${commitHash}"
                }
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

        stage('Publish') {
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
