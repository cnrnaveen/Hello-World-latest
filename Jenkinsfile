pipeline{
    agent any
    tools{
        maven 'maven'
    }
    environment {
        PATH = "/opt/maven/bin=$PATH"
    }
    
    stages{
        stage('SCM Checkout'){
            steps{
                git 'https://github.com/Vinayaka445/Hello-World-latest.git'
            }
        }
        stage('Maven Build'){
            steps{
                sh 'mvn clean install package'
            }
        }
    }
}
