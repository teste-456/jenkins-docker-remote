final String staging_docker_host = "ssh://jenkins@167.235.69.12"    
final String prod_docker_host = "ssh://root@167.235.76.166"

node {
    stage("Pull 2") {
        sh "docker pull nginx:latest"
    }
}

node {
    stage("Deploy Prod"){
        withEnv(["DOCKER_HOST=${staging_docker_host}"]) {
            sshagent( credentials: ['jenkins_docker']) {
                sh "docker -H ${prod_docker_host} run -d -p 80:80 nginx:latest"
            }
        }
    }
}