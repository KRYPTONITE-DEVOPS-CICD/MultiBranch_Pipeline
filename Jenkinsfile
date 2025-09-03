pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-clust', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://2B83F93BC121370073FFEE07CF36634B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-clust', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://2B83F93BC121370073FFEE07CF36634B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
