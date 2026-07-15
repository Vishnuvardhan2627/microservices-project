pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3C34F45AF6B9EDA1E548BF9CCBF0ABE7.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3C34F45AF6B9EDA1E548BF9CCBF0ABE7.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
