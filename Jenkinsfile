pipeline {
    agent any

    parameters {
        choice(
            name: 'ACTION',
            choices: ['apply', 'destroy'],
            description: 'Select whether to apply or destroy Terraform infrastructure'
        )
    }

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

        stage('Terraform Action') {
            steps {
                script {
                    if (params.ACTION == "destroy") {
                        sh '''
                          export PATH=$PATH:/opt/homebrew/bin
                          cd /Users/manish/Desktop/Provisioning/Terraform
                          terraform destroy -auto-approve
                        '''
                    } else {
                        sh '''
                          export PATH=$PATH:/opt/homebrew/bin
                          cd /Users/manish/Desktop/Provisioning/Terraform
                          terraform apply -auto-approve
                        '''
                    }
                }
            }
        }
    }
}
