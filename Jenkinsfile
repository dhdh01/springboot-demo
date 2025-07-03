pipeline {
    agent any

    environment {
        IMAGE_NAME = "springboot-demo"
        CONTAINER_NAME = "springboot-demo-container"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/dhdh01/springboot-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker rm -f ${CONTAINER_NAME} || true"
                sh "docker run -d --name ${CONTAINER_NAME} -p 8080:8080 ${IMAGE_NAME}"
            }
        }
    }
}
