pipeline {
    agent { label 'linux-agent' }
    stages {
//        stage('Checkout') {
//            steps {
//                checkout scm
//            }

//            agent {
//                label 'linux-agent'
//            }
//        }

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
                sh 'docker run -d --name opswerks-node-app  -p 3000:300 acad-node-app:latest'
             }

            agent {
                label 'linux-agent'
            }
        }
    }
}
