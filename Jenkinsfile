final String staging_docker_host = "ssh://jenkins@167.235.69.12"    
final String prod_docker_host = "ssh://root@167.235.76.166"

node {
    stage("Pull") {
        sh "docker pull  nginx:latest"
    }
}

node {
    stage("Deploy Prod"){
        sshagent( credentials: ['jenkins_docker']) {
            sh "docker -h ${prod_docker_host} run -d -p 80:80 nginx:latest"
        }
    }
}