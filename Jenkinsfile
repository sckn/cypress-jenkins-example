node {
    stage("Initalize") {
        def dockerHome = tool 'docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
        env.DOCKER_HOST =  "tcp://192-168-1-46.sslip.io:2375"
        sh "echo $PATH"
    }
}

pipeline {
    /*agent {
        docker { image 'node:16.13.1-alpine' }
    }*/
    stages {
        
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}
