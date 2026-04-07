pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-python-app .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'cat deployment.yaml | docker exec -i minikube sh -c "cat > /tmp/deployment.yaml"'
                sh 'cat service.yaml | docker exec -i minikube sh -c "cat > /tmp/service.yaml"'
                sh 'docker exec minikube bash -lc \'KUBECTL=$(find /var/lib/minikube/binaries -name kubectl | head -n 1); ls -l /tmp/deployment.yaml /tmp/service.yaml; $KUBECTL apply -f /tmp/deployment.yaml; $KUBECTL apply -f /tmp/service.yaml\''
            }
        }
    }
}
