pipeline {
    
    agent any
    triggers {  
        githubPush()  
    }  
    stages {
        stage('Removing old') {
            steps {
                sh 'rm -rf krsp-backend'
            }
        }
        stage('Checkout') {
            steps {
                sh 'mkdir krsp-backend'
                sh 'cd krsp-backend'
                sh 'git clone https://github.com/pratyush-kr/krsp-backend.git'
            }
        }
        stage('Docker build') {
            steps {
                sh 'docker build -t backend-app .'
            }
        }
        stage('Docker deploy') {
            steps {
                sh 'docker run -d -p 8000:8000 backend-app'
            }
        }
    }
}

