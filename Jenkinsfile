pipeline {
    agent any

    environment {
        IMAGE_NAME = "rehan282002/banking-app"
        CONTAINER_NAME = "banking-container"
        PORT = "8081"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/rehan282002/banking.git'
            }
        }

        stage('Build App') {
            steps {
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p $PORT:$PORT --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
