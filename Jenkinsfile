pipeline {
    agent any

    environment {
        IMAGE_NAME = "rehan282002/finance-app"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/rehan282002/banking.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f finance-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8081:8080 --name finance-app $IMAGE_NAME'
            }
        }
    }
}
