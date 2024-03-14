pipeline {
    agent any
        stages {
        stage('Checkout from Git') {
            steps {
                git branch: 'main', url: 'https://github.com/bkrrajmali/terraform-cicd-vm.git'
            }
        }
        stage('Install Terraform') {
            steps {
                script {
                    sh 'sudo yum install -y yum-utils'
                    sh 'sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo'
                    sh 'sudo yum -y install terraform'
                }
            }
        }
        stage('Run Terraform') {
            steps {
                script {
                    sh 'terraform --version'
                }
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
        stage('Terraform Destroy') {
            steps {
                sh 'terraform destroy -auto-approve'
            }
        }
    }
}
