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
    }
}
