final String staging_docker_host = "ssh://jenkins@167.235.69.12"    
final String prod_docker_host = "ssh://root@167.235.76.166"

node {
    stage("Pull") {
        sh "docker pull  nginx:latest"
    }

    stage('Sock') {
        agent {
            dockerfile {
                args '-u root:root -v /var/run/docker.sock:/var/run/docker.sock'
            }
        }
        steps {
                    sh  ''' echo 'hajsaks' '''                
        }
    }
    stage("Deploy Prod"){
        withEnv(["DOCKER_HOST=${staging_docker_host}"]) {
            sshagent( credentials: ['jenkins_docker']) {
                sh "docker -H ${prod_docker_host} run -d -p 80:80 nginx:latest"
            }
        }
    }

}