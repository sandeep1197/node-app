pipeline {
    agent {
    label "Slave-01"
    }
    tools {
    dockerTool "mydocker"
    }
    environment{
        DOCKER_TAG = getDockerTag()
    }
    stages{
        stage('Build Docker Image'){
            steps{
                sh "docker build . -t sandeep1197/node-app:${DOCKER_TAG}"
            }
        }
       stage('Push Image to docker hub') {
            steps{
                withCredentials([string(credentialsId: 'dockerhub', variable: 'dockerhub')]) {
                  sh 'docker login -u sandeep1197 -p ${dockerhub}'
                  sh 'docker push sandeep1197/node-app:${DOCKER_TAG}'
            
}
    }
}
}
}

def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}
