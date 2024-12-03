pipeline {
    agent { label 'linux-agent' }
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('build_dockerfile') {
            steps {
                docker.build('acad/node-app', './Dockerfile')
            }
        }

        stage('deploy_and_run') {
            steps {
                docker.image('acad/node-app:latest').withRun('-p 3000:3000')
            }
        }
    }
}
