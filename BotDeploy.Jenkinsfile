pipeline {
    agent any

    parameters {
        string(name: 'BOT_IMAGE_NAME')
    }

    stages {
        stage("Install Ansible") {
            steps {
                sh 'echo installing...'
            }
        }

        stage("Generate Ansible Inventory") {
            environment {
               
            }
            steps {
                sh 'echo Generating...'
            }
        }

        stage('Ansible Bot Deploy') {
            environment {
               
            }

            steps {
                sh 'echo deploying...'
                }
            }
        }
    }
