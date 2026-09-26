pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
        JOB_NAME = env.JOB_NAME
        BUILD_NUMBER = env.BUILD_NUMBER
    }

    stages {
        stage('Git Clone') {
            steps {
                git 'https://github.com/Abis2001/portfolio-project.git'
            }
        }
        stage('Check Files') {
            steps {
                sh '''
                echo "Current directory:"
                pwd

                echo "Files:"
                ls -la

                echo "Dockerignore:"
                cat .dockerignore || true

                echo "Index file:"
                ls -l index.html || true
        '''
        echo '.............................................................................................'
                }
        }

        stage('Build Docker Image') {
            steps {
        sh 'docker build -t abishek-portfolio:v1 .'
        echo '.............................................................................................'
                }
        }
        stage('Docker Login') {
            steps {
                withCredentials([
                 usernamePassword(
                credentialsId: 'dockerhub-credentials',
                usernameVariable: 'DOCKER_USERNAME',
                passwordVariable: 'DOCKER_PASSWORD'
            )
        ]) {
                sh '''
                echo "$DOCKER_PASSWORD" | docker login \
                -u "$DOCKER_USERNAME" \
                --password-stdin
                '''
        }
    }
}
        stage('Push to DockerHub') {
    steps {
        withCredentials([usernamePassword(
            credentialsId: 'dockerhub-credentials',
            usernameVariable: 'DOCKER_USERNAME',
            passwordVariable: 'DOCKER_PASSWORD'
        )]) {
            sh '''
                docker tag abishek-portfolio:v1 $DOCKER_USERNAME/portfolio:v1
                docker push $DOCKER_USERNAME/portfolio:v1
            '''
        }
    }
}
        stage('Old container remove') {
            steps {
                sh 'docker stop abishek-portfolio || true'
                sh 'docker rm abishek-portfolio || true'
                echo '.............................................................................................'
            }
        }
        stage('Docker run') {
            steps {
                sh 'docker run -d -p 8099:80 --name=abishek-portfolio abishek-portfolio:v1'
                echo '.............................................................................................'
            }
        }
    }
}