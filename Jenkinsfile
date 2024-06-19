pipeline { 
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                        sh "docker build -t neoop1/shippingservice:latest ."
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry([credentialsId: "docker-cred", url: "https://index.docker.io/v1/"]) { {
                        sh "docker push neoop1/shippingservice:latest "
                    }
                }
            }
        }
    }
}
