pipeline {
    agent { label 'linux-agent' }
    stages {
        stage('build_dockerfile') {
            steps {
                checkout scm
                def customImage = docker.build("acad/node-app:${env.BUILD_ID}")
                customImage.push('latest')
            }
        }

        stage('deploy_and_run') {
            steps {
                docker.image('acad/node-app:latest').withRun('-p 3000:3000')
            }
        }
    }
}
