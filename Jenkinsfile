pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://192.168.7.113:6443']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://192.168.7.113:6443']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
