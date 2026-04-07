stage('Deploy to Kubernetes') {
    steps {
        sh 'minikube kubectl -- apply -f deployment.yaml'
        sh 'minikube kubectl -- apply -f service.yaml'
    }
}
