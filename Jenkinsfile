pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out project...'
            }
        }

        stage('Test') {
            steps {
                bat 'C:/Users/dell/AppData/Local/Programs/Python/Python314/python.exe -m pytest'
            }
        }

        stage('Docker Image') {
            steps {
                bat 'docker images myapp:1.0'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
                bat 'kubectl apply -f k8s/service.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl rollout status deployment/myapp'
                bat 'kubectl get pods'
                bat 'kubectl get service myapp-service'
            }
        }
    }
}