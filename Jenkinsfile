pipeline{
    agent any
    parameters {
        booleanParam(defaultValue: false, description: 'Apply terraform changes?', name: 'applyChanges')
        booleanParam(defaultValue: false, description: 'Destroy terraform infrastructure?', name: 'destroyInfrastructure')
    }
    tools {
        terraform 'terraform'
    }
    stages{
        stage('checkout from GIT'){
            steps{
               git branch: 'main', url: 'https://github.com/RajaSekhar516/JenkinsCICD.git'
            }
        }
        stage('Terraform Init'){
            steps{
                sh 'terraform init'
            }
        }
        stage('Terraform Plan'){
            steps{
                sh 'terraform plan'
            }
        }
        stage('Terraform Apply'){
            when {
                expression { params.applyChanges }
            }
            steps{
                sh 'terraform apply --auto-approve'
            }
        }
        stage('Terraform Destroy'){
            when {
                expression { params.destroyInfrastructure }
            }
            steps{
                sh 'terraform destroy --auto-approve'
            }
        }
    }
}
