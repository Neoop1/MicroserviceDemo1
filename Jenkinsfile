pipeline {
    agent any
    environment {
        DOCKER_HUB = '192.168.7.121:9001/dockerhub'
    }
    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    dir('src') {

                    
                        sh "docker build -t $DOCKER_HUB/cartservice:latest ."
                    
                        }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'nexus-cred', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                        sh "docker login $DOCKER_HUB -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                        sh "docker push $DOCKER_HUB/cartservice:latest "
                    }
                }
            }
        }
    }
}
