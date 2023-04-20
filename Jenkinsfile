pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
    }
    stages {
        stage('test') {
            steps {
                script {
                    echo 'Hello World'
                }
            }
        }
        stage('build') {
            steps {
                script {
                    echo 'Changes made in build!'
                }
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('deploy') {
            steps {
                script {
                    def dockerCmd = 'sudo docker run -d -p 8080:80 nginx'
                    sshagent(['EC2-SERVER-KEY']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@3.127.151.251 ${dockerCmd}"
                    }
                }    
            }
        }      
    }     
}
