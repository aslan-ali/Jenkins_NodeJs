pipeline{
    agent any
    stages {
        stage("Test"){
            steps {
                sh "npm install"
                sh "npm test"
            }
        }
        stage("Build Image"){
            steps {
                sh 'docker build . -t netdevopsaslan/nodejs-application:latest'
            }
        }
        stage("Push Image"){
            steps {
                sh "docker login -u netdevopsaslan -p ${DOCKER_PASSWD}"
                sh "docker push netdevopsaslan/nodejs-application:latest"
            }
        }
    }
}
