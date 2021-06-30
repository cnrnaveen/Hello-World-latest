pipeline{
    agent any
    tools{
        maven 'M2_HOME'
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
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
