pipeline {
  agent {
    docker {
      image "node:8-alpine"
    }
  }
  stages {
    stage("Build") {
      steps {
        sh "chmod +x ./scripts/dropdb.sh"
        sh "npm install"
      }
    }
    stages("Test") {
      steps {
        sh "npm test:ci"
      }
    }
  }
}
