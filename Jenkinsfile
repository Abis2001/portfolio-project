pipeline {
    agent any

    stages {
        stage('Git Clone') {
            steps {
                git 'https://github.com/Abis2001/portfolio-project.git'
            }
        }
        stage('Docker build') {
            steps {
                sh 'docker build -t abishek-portfolio:v1 .'
            }
        }
        stage('Old container remove') {
            steps {
                sh 'docker stop abishek-portfolio || true'
                sh 'docker rm abishek-portfolio || true'
            }
        }
        stage('Docker run') {
            steps {
                sh 'docker run -d -p 8099:80 --name=abishek-portfolio abishek-portfolio:v1'
            }
        }
    }
}