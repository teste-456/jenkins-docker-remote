final String staging_docker_host = "ssh://jenkins@localhost"    
final String prod_docker_host = "ssh://root@167.235.69.12"

node {
    stage("Pull") {
        sh "docker pull nginx:latest"
    }

    stage("Deploy Prod"){
      withEnv(["DOCKER_HOST=${staging_docker_host}"]) {
            sshagent( credentials: ['teste']) {
                //sh "docker -H ${prod_docker_host} run -d -p 80:80 nginx:latest"
                sh "docker -H ${prod_docker_host} run -d -p 81:81 nginx:latest"
            }
        } 
    }

}