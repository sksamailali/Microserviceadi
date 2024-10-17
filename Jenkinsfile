pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image1') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t sksamailali/checkoutservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push sksamailali/checkoutservice:latest "
                    }
                }
            }
        }
    }
}
