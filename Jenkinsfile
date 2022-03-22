def image

pipeline {
    agent any
    stages {
        stage('Build') {   
            steps {
                script {
                    container = image('nginx').withRun('-p 9090:9090')
                    //container.stop()
              }
            }
        }
        stage('Push') {                 
            steps { 
                script {
                    withDockerRegistry([credentialsId: "docker-hub", url: "https://hub.docker.com/repository/docker/macprasanna/private_repo" ]) {        
                        image.push()
                    }     
                }
            }
        }
    }
}
