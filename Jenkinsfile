pipeline {
    agent { label 'linux-agent' }
    stages {
        stage('build_dockerfile') {
            steps {
                checkout scm
                def app = docker.build('acad/node-app', './Dockerfile')
                app.push()
            }
        }

        stage('deploy_and_run') {
            steps {
                docker.image('acad/node-app:latest').withRun('-p 3000:3000')
            }
        }
    }
}
