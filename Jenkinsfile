pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Ramya249/CandyStore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'dock', toolName: 'docker') {
                         sh 'docker build -t ramya249/candystore .'
                         sh 'docker push ramya249/candystore:latest'
                   }
               }
            }
        }
    }
}
