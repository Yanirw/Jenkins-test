pipeline {
    agent any

    stages {
        stage('build app') {
            steps {
               script {
                echo "building!"
               }
            }
        }

        stage('Build') {
            steps {
                script {
                  echo "building docker image..."
                }
            }
        }

        stage('Deploy') {
          environment {
            AWS_ACCESS_KEY_ID = credentials('aws_access_key_id')  
            AWS_SECRET_ACCESS_KEY = credentials('aws_secret_access_key')
          }
            steps {
                // Add steps to deploy your application
                script {
                  sh 'kubectl create deployment nginx-deployment --image=nginx'
                }
            }
        }
    }
