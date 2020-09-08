pipeline {
  agent {
    docker {
    image "node:10-alpine"
    args "--network=skynet"
    }
  }
  stages {
     stage ("Build") {
       steps {
         sh "chmod +x ./scripts/alpine.sh && ./scripts/alpine.sh"
         sh "chmod +x ./scripts/dropdb.sh"
         sh "npm install"
       }
     }
    stage ("Test"){
      steps {
        sh "npm run test:ci"
      }
      post{
        always {
          junit "log/*.xml"
        }
      }
    }
    stage("Production"){
      steps {
      input message: "Go to production?(Clik 'Proceed' to continue)"
      sh "echo 'Subindo em produção'"
      }
    }
  }
}
