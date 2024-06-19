pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                        sh "docker build -t neoop1/adservice:latest ."
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry('https://registry-1.docker.io/v2/' credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push neoop1/adservice:latest "
                    }
                }
            }
        }
    }
}
