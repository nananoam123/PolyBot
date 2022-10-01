pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo building...'
                sh'export AWS_ACCESS_KEY_ID=AKIAQP7LUWAEGOXLVXWK'
                sh'export AWS_SECRET_ACCESS_KEY=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'
                sh'export AWS_DEFAULT_REGION=eu-west-1'
                sh '/usr/local/bin/aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/b1o7b4g2'
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
