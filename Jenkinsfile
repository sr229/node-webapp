pipeline {
    agent { label 'linux-agent' }
    stages {
        stage('Checkout') {
            steps {
             checkout scm
            }

            agent {
                label 'linux-agent'
            }
        }

        stage('Docker Build') {
            steps {
                docker.build('acad-node-app')
            }

            agent {
                label 'linux-agent'
            }
        }

        stage('Deploy and Run') {
            steps {
                docker.image('acad-node-app').withRun('-p 3000:3000') {
                    sh 'npm start'
                }
             }

            agent {
                label 'linux-agent'
            }
        }
    }
}
