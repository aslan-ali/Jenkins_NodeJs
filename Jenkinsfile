pipeline{
    agent any
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages {
        stage("Clean Up"){
            steps {
                deleteDir()
            }
        }
        stage("Test"){
            steps {
                sh "npm run test"
                sh "npm install"
            }
        }
        stage("Build Image"){
            steps {
                sh 'docker build -t netdevopsaslan/nodejs-application:latest'
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
