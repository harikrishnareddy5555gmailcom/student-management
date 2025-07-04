pipeline {
    agent any

    environment {
        DOCKER_HUB_USER = 'harik0105'
        IMAGE_NAME = 'student-management'
    }

    stages {
        stage('Clone Source Code') {
            steps {
                git 'https://github.com/harikrishnareddy5555gmailcom/student-management.git'
            }
        }

        stage('Build JAR') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_HUB_USER}/${IMAGE_NAME} ."
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-creds', url: '']) {
                    sh "docker push ${DOCKER_HUB_USER}/${IMAGE_NAME}"
                }
            }
        }
    }
}
