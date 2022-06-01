final String staging_docker_host = "ssh://jenkins@167.235.69.12"    
final String prod_docker_host = "ssh://root@167.235.76.166"

node {
    stage("Pull") {
        sh "docker pull nginx:latest"
    }

    stage("Deploy Prod"){
        sshagent( credentials: ['8aeaee5e-8fce-4e52-b0f8-d0a5db261a52']) {
            sh "docker -H ${prod_docker_host} run -d -p 80:80 nginx:latest"
        }
    }

}