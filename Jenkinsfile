pipeline {
    agent any
    environment {
        SERVICE = 'db'
        NAME = "benisli/${env.SERVICE}"
    }
    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'aws-credentials'
                ]]) {
                    sh '''
                        aws eks update-kubeconfig --name eks-store --region us-east-2
                        kubectl apply -f k8s/k8s.yaml
                    '''
                }
            }
        }
    }
}