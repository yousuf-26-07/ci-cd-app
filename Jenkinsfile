pipeline {
    agent any

    environment {
        IMAGE_NAME = "yousuf2023bcs0013/cicd_app"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/yousuf-26-07/ci-cd-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $cicd_app .'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-credentials', usernameVariable: 'yousuf2023bcs0013', passwordVariable: 'Yousuf@2607')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push $cicd_app'
            }
        }
    }
}
