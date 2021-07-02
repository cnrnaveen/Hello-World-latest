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
                git credentialsId: 'Git', url: 'https://github.com/Vinayaka445/Hello-World-latest.git'
            }
        }
        stage('Maven Build'){
            steps{
                sh 'mvn clean install package'
                sh 'mv target/.war target/myweb.war'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy-to-Tomcat-dev'){
            steps{
            sshagent(['Tomcat-user']) {
                sh """
                     scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.13.2:/opt/tomcat8/webapps/
                     
                     ssh ec2-user@172.31.13.2 /opt/tomcat8/bin/shutdown.sh
                     
                     ssh ec2-user@172.31.13.2 /opt/tomcat8/bin/startup.sh
                
                """
             }
            } 
        }
    }
}
