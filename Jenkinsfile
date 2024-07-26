pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                   withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8076F305984BF857E038E9C419DC17D2.gr7.ap-south-1.eks.amazonaws.com']]) {
                      sh "kubectl apply -f deployment-service.yml"
                     sleep 60
        }
               
     }
}
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8076F305984BF857E038E9C419DC17D2.gr7.ap-south-1.eks.amazonaws.com']]) {
                      sh "kubectl get svc -n webapps"
                 
               }
            }
        }
    }
}
