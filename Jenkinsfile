pipeline {
    agent any
    stages {
        stage('Build') {   
            steps {
                script {
                    def image = docker.image('nginx');
                    image.pull()
                    container = image.run()
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
