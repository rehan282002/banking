pipeline {
    agent any
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
                sh 'docker build -t rehan282002/finance-app .'
            }
        }
        stage('Remove Old Container') {
            steps {
                sh 'docker rm -f finance-container || true'
            }
        }
        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8081:8080 --name finance-container rehan282002/finance-app'
            }
        }
    }
}
