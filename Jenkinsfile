pipeline {
    agent any
    environment {
        DOCKER_HUB = '192.168.7.121:9001/dockerhub'
    }
    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                        sh "docker build -t $DOCKER_HUB/shippingservice:latest ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'nexus-cred', toolName: 'docker') {
                        sh 'docker push $DOCKER_HUB/shippingservice:latest '

                    }
                }
            }
        }
    }
}