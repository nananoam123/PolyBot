pipeline {
    agent any
     environment {
        REGISTRY_URL = "public.ecr.aws/b1o7b4g2"
        IMAGE_TAG = "0.0.$BUILD_NUMBER"
        IMAGE_NAME = "noam-repo"
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo building...'
                sh'export AWS_PROFILE= default'
                sh '/usr/local/bin/aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin $REGISTRY_URL'
                sh 'docker build -t $REGISTRY_URL/$IMAGE_NAME:$IMAGE_TAG .'
                sh 'docker push $REGISTRY_URL/$IMAGE_NAME:$IMAGE_TAG'
            }
            
        }
        
        stage('prune') {
            steps {
                sh 'echo "stage II..."'
                post {
                always {
                    sh '''
                    docker image prune -f --filter "until=240h"
                    '''
                }
            }
            }
        }
        stage('Trigger Deploy') {
            steps {
                build job: 'BotDeploy', wait: false, parameters: [
                    string(name: 'BOT_IMAGE_NAME', value: "$REGISTRY_URL/$IMAGE_NAME:$IMAGE_TAG")
                ]
            }
        }
    }
}
