pipeline {
    agent { docker { image 'docker' } }
    stages {
        stage("Build"){
            steps {
                sh "docker build . -t netdevopsaslan/nodes-apps:latest"
            }
        }
        stage("Push Image"){
            steps {
                sh "docker login -u netdevopsaslan -p ${DOCKER_PASSWD}"
                sh "docker push netdevopsaslan/nodejs-apps:latest"
            }
        }
    }
}
