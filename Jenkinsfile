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
    }
}

def getDockerTag(){
    def tag  = sh script: 'git rev-parse HEAD', returnStdout: true
    return tag
}
