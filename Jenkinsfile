pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/your-repo/demo.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t springboot-app .'
            }
        }

        stage('Deploy') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline Failed!'
        }
    }
}