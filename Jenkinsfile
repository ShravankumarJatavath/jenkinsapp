pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ShravankumarJatavath/jenkinsapp.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh """
                docker build -t my-k8s-app:${BUILD_NUMBER} .
                docker tag my-k8s-app:${BUILD_NUMBER} jatavathshravan/my-k8s-app:${BUILD_NUMBER}
                """
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker push jatavathshravan/my-k8s-app:${BUILD_NUMBER}"
            }
        }
    }
}