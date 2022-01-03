node {
    stage("Initalize") {
        def dockerHome = tool 'docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
        env.DOCKER_HOST =  "tcp://192-168-1-46.sslip.io:2375"
        sh "echo $PATH"
    }
}


pipeline {
    agent {
        node { label 'built-in' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'docker run -i cypress/base:10 node --version'
            }
        }
    }
}
