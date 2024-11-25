pipeline {
    agent any
    
    environment{
        DOCKER_CREDENTIALS_ID = 'dockerhub-pass-login'
        DOCKERHUB_REPO = 'egorlegeyda/task12'
        REMOTE_SERVER = 'ubuntu@54.209.192.114'
        IMAGE_NAME_NGINX = 'egorlegeyda/task12:nginx'
        IMAGE_NAME_PHP = 'egorlegeyda/task12:php'
    }
    
    
    stages{
        stage('build docker image'){
            steps{
                script{
                    sh "pwd"
                    docker.build(IMAGE_NAME_PHP, './apache')
                    docker.build(IMAGE_NAME_NGINX, './nginx')
                    sh "docker images"
                }
            }
        }
        stage('Push to dockerhub'){
            steps{
                script{
                        sh "docker images"
                        docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID){
                        docker.image(IMAGE_NAME_NGINX).push()
                        docker.image(IMAGE_NAME_PHP).push()
                    }
                }
            }
        }
        stage('Deploy to Remote Server') {
            steps {
                script {
                    sshagent(['second-key.pem']) { // ID ваших SSH учетных данных
                        // sh """
                        // ssh ${REMOTE_SERVER} 'docker pull ${IMAGE_NAME_NGINX} &&
                        // docker pull ${IMAGE_NAME_PHP}
                        // docker stop my_container || true &&
                        // docker rm my_container || true &&
                        // docker run -d --name my_container ${IMAGE_NAME}'
                        // """
                        sh """
                        ssh ${REMOTE_SERVER}
                            'if [ \"\$(docker ps -aq)\" ]; then
                                docker rm -f \$(docker ps -aq)
                            fi

                            if [ \"\$(docker images -q)\" ]; then
                                docker rmi \$(docker images -q)
                            fi

                            docker pull egorlegeyda/task12:nginx &&
                            docker pull egorlegeyda/task12:php &&

                            docker run --network mynetwork --name php-container -d -p 8081:8081 egorlegeyda/task12:php &&
                            docker run --network mynetwork --name nginx-container -d -p 80:80 egorlegeyda/task12:nginx'
                        """
                    }
                }
            }
        }

    }
}