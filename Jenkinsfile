pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/MittaSoumya/k8s.git'
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
                docker build -t my-k8s:${BUILD_NUMBER} .
                docker tag my-k8s:${BUILD_NUMBER} mittasoumya/my-k8s:${BUILD_NUMBER}
                '''
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push mittasoumya/my-k8s:${BUILD_NUMBER}'
            }
        }

        
            
        }
    }
