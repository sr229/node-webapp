pipeline {
    agent { label 'linux-agent' }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Docker Build') {
            steps {
                script {
                    docker.build('acad-node-app')
                }
            }
        }

        stage('Deploy and Run') {
            steps {
                sh 'docker run -d --name opswerks-node-app  -p 3000:300 acad-node-app:latest'
            }
        }
    }
}
