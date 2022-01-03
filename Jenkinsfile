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
        docker { image 'node:16.13.1-alpine' }
    }
    stages {
        stage('ENV test') {
            steps {
                sh "echo 'echo hello' > test_script"
                sh "chmod +x ./test_script"
                withEnv(["PATH+EXTRA=${WORKSPACE}"]) {
                    sh "env | grep PATH"
                    sh "node --versio"
                }
            }
        }
    }
}
