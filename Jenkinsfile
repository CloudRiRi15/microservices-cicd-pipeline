pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {  
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t cloudriri15/emailservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push cloudriri15/emailservice:latest "
                    }
                }
            }
        }
    }
}
