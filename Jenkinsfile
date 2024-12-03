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
                sh 'docker stop opswerks-node-app && docker rm opswerks-node-app'
                sh 'docker run -d --name opswerks-node-app  -p 3000:3000 acad-node-app:latest'
            }
        }
    }
}
