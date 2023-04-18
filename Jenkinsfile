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
                    echo 'Hello World'
                }
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('deploy') {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: 'EC2-SERVER-KEY', keyFileVariable: 'EC2_SERVER_KEY')]) {
                        sh '''
                          set -e
                          TEMP_KEY=$(mktemp)
                          echo "$EC2_SERVER_KEY" > $TEMP_KEY
                          chmod 600 $TEMP_KEY
                          ssh -i $TEMP_KEY -o StrictHostKeyChecking=no ec2-user@3.76.28.241 sudo docker run -d -p 8080:80 nginx
                          rm -f $TEMP_KEY
                        '''
                    }
                }    
            }
        }      
    }     
}
