pipeline {
    agent any
    stages {
        stage('Terraform Init') {
            steps {
                sh '''
                  export PATH=$PATH:/opt/homebrew/bin
                  cd /Users/manish/Desktop/Provisioning/Terraform
                  terraform init
                '''
            }
        }
        stage('Terraform Apply') {
            steps {
                sh '''
                  export PATH=$PATH:/opt/homebrew/bin
                  cd /Users/manish/Desktop/Provisioning/Terraform
                  terraform apply -auto-approve
                '''
            }
        }
    }
}
