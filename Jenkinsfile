stage('Deploy to Kubernetes') {
    steps {
        sh 'docker cp deployment.yaml minikube:/tmp/deployment.yaml'
        sh 'docker cp service.yaml minikube:/tmp/service.yaml'
        sh 'docker exec minikube kubectl apply -f /tmp/deployment.yaml'
        sh 'docker exec minikube kubectl apply -f /tmp/service.yaml'
    }
}
