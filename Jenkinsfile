pipeline{
    agent any
    stages("Build Image"){
        steps {
            sh "docker build . -t netdevopsaslan/nodejs-apps:latest"
        }
    }
    stage("Push Image"){
        steps {
            sh "docker login -u netdevopsaslan -p ${DOCKER_PASSWD}"
            sh "docker push netdevopsaslan/nodejs-apps:latest"
        }
    }
}
