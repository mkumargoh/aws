pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = "us-east-1"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Terraform Init') {
            steps {
                sh '''
                terraform init
                '''
            }
        }
        stage('Terraform Plan') {
            steps {
                sh '''
                terraform plan -out=tfplan
                '''
            }
        }
        stage('Terraform Apply') {
            when {
                branch 'main'
            }
            steps {
                sh '''
                terraform apply -auto-approve tfplan
                '''
            }
        }
    }
}
