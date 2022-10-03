pipeline {
    agent any
    stages {
        stage("Build image"){
            sh "docker build . -t netdevopsaslan/nodejs-apps:latest"
        }
    }
}
