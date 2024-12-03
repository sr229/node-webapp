pipeline {
    agent { label 'linux-agent' }
    stages {
        stage('Checkout') {
            steps {
                checkout
            }

            agent {
                label 'linux-agent'
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    docker.build('acad-node-app')
                }
            }

            agent {
                label 'linux-agent'
            }
        }

        stage('Deploy and Run') {
            steps {
                script {
                    docker.image('acad-node-app').withRun('-p 3000:3000') {
                        sh 'npm start'
                    }
                }
             }

            agent {
                label 'linux-agent'
            }
        }
    }
}
