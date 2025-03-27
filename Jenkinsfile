pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Lele2001avie/Backend-API-Express',
                        credentialsId: 'github-credentials'
                    ]]
                ])
            }
        }
         // installer les librairies
         stage('Installs') {
            steps {
                   sh 'npm install --force'
                   sh 'npm install mocha --save-dev'
            }
         }
        // Test unitaires en utilisent la librairie mocha
        stage('Test') {
            steps {
                sh 'npm test'
             }
        }
        
        // Creation image docker 
        stage('build_docker'){
            steps{
                sh 'docker build -t jenkins-node .'
            }
        }
        
        // push docker image 
        
        stage('Push Docker Image') {
            steps {
                script {

                    withCredentials([usernamePassword(credentialsId: 'docker_credentiel', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                        sh 'echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin'
                        sh "docker tag jenkins-node lealouise2001avie/eval_9avril:latest "  // Tag l’image
                        sh "docker push lealouise2001avie/eval_9avril:latest "  // Push l’image sur Docker Hub
                    }
                }
            }
        }

    }
}
