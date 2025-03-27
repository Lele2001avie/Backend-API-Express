pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Lele2001avie/Docker_jenkins.git',
                        credentialsId: 'github-credentials'
                    ]]
                ])
            }
        }
        // stage('Build') {
        //     steps {
        //         // TODO
        //     }
        // }
        // stage('Test') {
        //     steps {
        //         // TODO
        //     }
        // }
    }
}