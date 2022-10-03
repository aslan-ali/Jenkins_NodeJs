pipeline {
    agent any
    environment {
        tag = sh(returnStdout: true, script: "git rev-parse -short=10 HEAD | tail -n +2")
    }
    stages{
        stage('Build docker image'){
            steps{
                script{
                    sh "docker build -t netdevopsaslan/nodejs-apps:${var.tag}"
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'DOCKER_PASSWD', variable: 'DOCKER_PASSWD')]) {
                   sh 'docker login -u netdevopsaslan -p ${DOCKER_PASSWD}'

}
                   sh 'docker push netdevopsaslan/nodejs-apps:${var.tag}'
                }
            }
        }
