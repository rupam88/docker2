pipeline {

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git url:'https://github.com/rupam88/docker2.git', branch:'main'
      }
    }
    
      stage("Build image") {
            steps {
                script {
                    myapp = docker.build("rupsdan/hellowhale:${env.BUILD_ID}")
                }
            }
        }
    
      stage("Push image") {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') {
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }

    
   // stage('Deploy App') {
     // steps {
        //script {
         // kubernetesDeploy(configs: "hellowhale.yml", kubeconfigId: "mykubeconfig")
       // }
     // }
   // }

  }

}
