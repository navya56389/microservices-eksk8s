pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://72BCFF29B6B4C3AB46A5AB48C1CD71F0.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://72BCFF29B6B4C3AB46A5AB48C1CD71F0.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
