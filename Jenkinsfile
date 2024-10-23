pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                 withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C84723FEC70D9DB87A2632FE99C9C447.gr7.us-east-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C84723FEC70D9DB87A2632FE99C9C447.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
