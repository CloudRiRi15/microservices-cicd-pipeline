pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' eks-mciroservice', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://84D54FB3773FF9409BD7701FD10FE847.gr7.af-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' eks-mciroservice', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://84D54FB3773FF9409BD7701FD10FE847.gr7.af-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get service -n webapps"   
                }
            }
        }    
    }
}
