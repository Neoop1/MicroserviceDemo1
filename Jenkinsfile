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
    }  
    stage('Docker Push') {
            agent any
            steps {
                 withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                 sh 'docker push neoop1/shippingservice:latest'      
        }
      }
    }
  }
}