pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' samail-eks1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF10A477A4384E93AEE5303E502074C8.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' samail-eks1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF10A477A4384E93AEE5303E502074C8.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
