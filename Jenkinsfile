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
                sh 'docker cp deployment.yaml minikube:/tmp/deployment.yaml'
                sh 'docker cp service.yaml minikube:/tmp/service.yaml'
                sh 'docker exec minikube bash -lc \'KUBECTL=$(find /var/lib/minikube/binaries -name kubectl | head -n 1); $KUBECTL apply -f /tmp/deployment.yaml\''
                sh 'docker exec minikube bash -lc \'KUBECTL=$(find /var/lib/minikube/binaries -name kubectl | head -n 1); $KUBECTL apply -f /tmp/service.yaml\''
            }
        }
    }
}
