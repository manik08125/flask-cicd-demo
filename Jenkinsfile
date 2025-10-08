pipeline {
    agent any

    environment {
        IMAGE_NAME = 'flask-cicd-demo'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-github-username/flask-cicd-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:${BUILD_NUMBER}")
                }
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop flask-cicd-demo || true
                docker rm flask-cicd-demo || true
                docker run -d -p 5000:5000 --name flask-cicd-demo ${IMAGE_NAME}:${BUILD_NUMBER}
                '''
            }
        }
    }
}
