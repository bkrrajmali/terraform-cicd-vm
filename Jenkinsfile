pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your/repo.git'
            }
        }
        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform Plan') {
            steps {
                sh 'terraform plan'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
       stage('Approval') {
            steps {
                // Pause pipeline and wait for user input
                input message: 'Deploy to production?', ok: 'Deploy'
            }
        }
      stage('Terraform Apply') {
            steps {
                sh 'terraform destroy -auto-approve'
            }
        }
    }
}
