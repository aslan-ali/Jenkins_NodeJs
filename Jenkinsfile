pipeline{
    agent any
    stages {
        stage("Build Image"){
            steps {
                sh "docker build . -t netdevopsaslan/nodejs-apps:${env.BUILD_NUMBER}"
            }
        }
        stage("Stage Login"){
            steps {
                script {
                withCredentials([string(credentialsId: 'DOCKER_PASSWD', variable: 'DOCKER_PASSWD')]) {
                   sh 'docker login -u netdevopsaslan -p ${DOCKER_PASSWD}'
                }
                sh 'docker push netdevopsaslan/nodejs-apps:${env.BUILD_NUMBER}'
            }
        }
        stage("Deploy to Kubernetes"){
            steps {
                script {
                kubeconfig(credentialsId: 'aslan', serverUrl: 'https://172.16.8.19:6443') {
                   sh "kubectl get pods "
               }
               } 
            }
        }
    }
    }
}
