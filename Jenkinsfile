pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean install package'
            }
        }
    }
    stages {
        stage ('Test') {
            steps {
                echo 'Testing....'
            }
        }
    }
    stages {
        stage ('Deploy') {
            steps {
                echo 'Deploying......'
            }
        }
    }
}
