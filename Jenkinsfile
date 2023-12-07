pipeline {
    agent any

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    sh "docker build -t arul:$GIT_COMMIT ."
                }
            }
        }

        stage('Stop and Remove Existing Container') {
            steps {
                script {
                    sh "docker stop arul || true"
                    sh "docker rm arul || true"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker run -p 8081:8080 --name arul -d arul arul:$GIT_COMMIT"
                }
            }
        }
    }
}
