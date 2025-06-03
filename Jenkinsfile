pipeline {
    agent any
    environment {
        SERVICE = 'db'
        NAME = "benisli/${env.SERVICE}"
    }
    stages {
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/k8s.yaml'
            }
        }
    }
}