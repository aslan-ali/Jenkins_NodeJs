pipeline {
    agent any
    stages {
        stage("Build Image"){
            steps {
                sh "docker build . -t netdevopsaslan/nodejs-apps:${env.BUILD_NUMBER}"
            }
        }
    }
}
