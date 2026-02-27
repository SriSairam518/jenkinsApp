pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SriSairam518/jenkinsApp.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t jenkinsapp:${BUILD_NUMBER} .
                docker tag jenkinsapp:${BUILD_NUMBER} valakatisrisairam/jenkinsapp:${BUILD_NUMBER}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push valakatisrisairam/jenkinsapp:${BUILD_NUMBER}'
            }
        }
    }
}
