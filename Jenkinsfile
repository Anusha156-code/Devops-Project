pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/Anusha156-code/Devops-Project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp .'
            }
        }

        stage('Stop Old Container (if any)') {
            steps {
                sh '''
                docker stop myapp-container || true
                docker rm myapp-container || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name myapp-container myapp'
            }
        }
    }
}
