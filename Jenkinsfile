pipeline {
    agent any
    environment {
        tag =  sh(returnStdout: true, script: "git rev-parse -short=10 HEAD | tail -n +2")
    }
    stages{
        stage('build image'){
            steps {
                sh "docker build . -t netdevopsaslan/nodejs-apps:$(env.tag)"
            }
        }
    }
}
