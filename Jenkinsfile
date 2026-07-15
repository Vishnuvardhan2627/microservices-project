pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://21F1486C2D24D5ADE6CA777AE6D8C914.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://21F1486C2D24D5ADE6CA777AE6D8C914.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
