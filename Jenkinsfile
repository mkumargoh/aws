pipeline {
    agent any
    stages {
        stage('User Input') {
            steps {
                script {
                    def ACTION = input(
                        id: 'userInput', 
                        message: 'Choose an action for Terraform:', 
                        parameters: [
                            choice(
                                choices: ['apply', 'destroy'], 
                                description: 'Select whether to apply or destroy infrastructure.', 
                                name: 'ACTION'
                            )
                        ]
                    )
                    env.ACTION = ACTION
                }
            }
        }

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
                    if (env.ACTION == "destroy") {
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
