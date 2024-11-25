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
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS_ID){
                        docker.image(IMAGE_NAME_NGINX).push()
                        docker.image(IMAGE_NAME_PHP).push()
                    }
                }
            }
        }
    }
}