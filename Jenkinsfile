final String staging_docker_host = "ssh://jenkins@localhost"    
final String prod_docker_host = "ssh://root@167.235.76.166"

node {
    stage("Pull") {
        sh "docker pull nginx:latest"
    }

    stage("Deploy Prod "){
      withEnv(["DOCKER_HOST=${staging_docker_host}"]) {
            sshagent( credentials: ['teste']) {
                //sh "ssh root@167.235.76.166 -i ~/.ssh/teste"
                sh "docker -H ${prod_docker_host} run -d -p 80:80 nginx:latest"
            }
        } 
    }

}