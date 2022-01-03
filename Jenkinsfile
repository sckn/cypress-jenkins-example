node {
    stage("Initalize") {
        def dockerHome = tool 'docker'
        env.PATH = "${dockerHome}/bin:${env.PATH}"
        env.DOCKER_HOST =  "tcp://192-168-1-46.sslip.io:2375"
        sh "echo $PATH"
    }
}

pipeline {
     stages {
     stage('Build') {
   agent {
        // Cannot use docker agent type because image will not be pulled fresh
        // each time. Instead, manually insert docker pull then run with the
        // the docker image.
        node {
          label 'node'
        }
      }
    
    steps {
    
       sh 'docker pull node:16.13.1-alpine'
       timeout(time: 15, unit: "MINUTES") {

          withDockerContainer(image: 'node:16.13.1-alpine', toolName='docker') {
            sh '''
              node --version
            '''
          }
            
        }
    }
    }  
    }
   
}
