pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'My-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CC36A7238A930914E96CD64E24FFC690.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'My-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CC36A7238A930914E96CD64E24FFC690.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
