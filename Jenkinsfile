// Jenkins Pipeline script for Terraform CI/CD

pipeline {
    agent any

    environment {
        //GIT_REPO = 'https://github.com/your-org/your-terraform-repo.git' // Replace with your repository URL will be used only if not configuring SCM pipeline
        //BRANCH = 'main' // Replace with your branch name
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')          // AWS Access Key (stored in Jenkins Credentials)
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')     // AWS Secret Key (stored in Jenkins Credentials)
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    // Clone the Terraform code from GitHub
                    git branch: main, url: 'https://github.com/pankajsao11/serverless-webapp.git'
                }
            }
        }

        stage('Terraform Init') {
            steps {
                script {                    
                    sh 'terraform init'  // Initialize Terraform
                }
            }
        }

        stage('Terraform Validate') {
            steps {
                script {                    
                    sh 'terraform validate'  // Terraform validate for syntax checking
                }
            }
        }

        stage('Terraform format') {
            steps {
                script {                    
                    sh 'terraform fmt --recursive' // Terraform format for formatting code
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                script {
                    // Generate and display the Terraform execution plan
                    sh 'terraform plan'
                }
            }
        }

        stage('Terraform Apply') {
            when {
                expression {
                    // Run terraform apply only for non-PR environments or specific conditions
                    return params.APPLY_CHANGES == true
                }
            }
            steps {
                script {
                    // Apply the Terraform changes
                    sh 'terraform apply -auto-approve'
                }
            }
        }
    }

    post {
        always {
            // Clean up workspace after execution
            cleanWs()
        }
        success {
            echo 'Terraform pipeline executed successfully!'
        }
        failure {
            echo 'Terraform pipeline failed. Please check logs!'
        }
    }
}




==========================================================================================================================================================
//by using pipeline syntax generator
pipeline {
    agent any

    environment {
        //GIT_REPO = 'https://github.com/your-org/your-terraform-repo.git' // Replace with your repository URL will be used only if not configuring SCM pipeline
        //BRANCH = 'main' // Replace with your branch name
        AWS_ACCESS_KEY     = credentials('AWS_ACCESS_KEY')          // AWS Access Key (stored in Jenkins Credentials)
        AWS_SECRET_KEY = credentials('AWS_SECRET_KEY')     // AWS Secret Key (stored in Jenkins Credentials)
    }
    
    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/pankajsao11/serverless-webapp.git'
            }
        }
    
        stage('Terraform fmt'){
            steps{
                sh 'terraform fmt --recursive'
            }
        }
    
        stage('Terraform init'){
            steps{
                sh 'terraform init'
            }
        }
        
        stage('Terraform validate'){
            steps{
                sh 'terraform validate'
            }
        }
        
        stage('Terraform plan'){
            steps{
                sh 'terraform plan'
            }
        }
    }
}


//erro message:
Started by user admin
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/jenkins_home/workspace/Git
[Pipeline] {
[Pipeline] withCredentials
Masking supported pattern matches of $AWS_SECRET_KEY or $AWS_ACCESS_KEY
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Git Checkout)
[Pipeline] git
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/pankajsao11/serverless-webapp.git
 > git init /var/jenkins_home/workspace/Git # timeout=10
Fetching upstream changes from https://github.com/pankajsao11/serverless-webapp.git
 > git --version # timeout=10
 > git --version # 'git version 2.39.5'
 > git fetch --tags --force --progress -- https://github.com/pankajsao11/serverless-webapp.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/pankajsao11/serverless-webapp.git # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 09968464394d57747fe8f8454aacf60aeae17c58 (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 09968464394d57747fe8f8454aacf60aeae17c58 # timeout=10
 > git branch -a -v --no-abbrev # timeout=10
 > git checkout -b main 09968464394d57747fe8f8454aacf60aeae17c58 # timeout=10
Commit message: "Update Jenkinsfile"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Terraform fmt)
[Pipeline] sh
+ terraform fmt --recursive
/var/jenkins_home/workspace/Git@tmp/durable-539d1700/script.sh.copy: 1: terraform: not found
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Terraform init)
Stage "Terraform init" skipped due to earlier failure(s)
[Pipeline] getContext
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Terraform validate)
Stage "Terraform validate" skipped due to earlier failure(s)
[Pipeline] getContext
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Terraform plan)
Stage "Terraform plan" skipped due to earlier failure(s)
[Pipeline] getContext
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withCredentials
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
ERROR: script returned exit code 127
Finished: FAILURE

