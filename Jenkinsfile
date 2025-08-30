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
                cd EC2_VPC
                terraform init
                '''
            }
        }
        stage('Terraform Plan') {
            steps {
                sh '''
                cd EC2_VPC
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
                cd EC2_VPC
                terraform apply -auto-approve tfplan
                '''
            }
        }
    }
}
