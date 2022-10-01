pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo building...'
                sh'export AWS_PROFILE= default'
                sh '/usr/local/bin/aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/b1o7b4g2'
                sh 'docker build -t noam-repo:${env.BUILD_NUMBER} .'
                sh 'docker push public.ecr.aws/b1o7b4g2/noam-repo:${env.BUILD_NUMBER}'
            }
        }
        stage('Stage II') {
            steps {
                sh 'echo "stage II..."'
            }
        }
        stage('Stage III ...') {
            steps {
                sh 'echo echo "stage III..."'
            }
        }
    }
}
