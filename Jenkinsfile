pipeline {
    agent any

    tools {
        
       maven 'Apache Maven 3.8.7'
    }

    stages {
        stage('git checkout scm') {
            steps {
                git 'https://github.com/mmbabu1988/build-deploy.git'
                
            }
        }
        stage('Build the maven code') {
            steps {
                sh 'mvn clean install'
                
            }
        }
        stage('Deploy the code into the tomcat server') {
            steps {
               deploy adapters: [tomcat9(credentialsId: 'tomcat_password', path: '', url: 'http://65.0.203.172:8090/')], contextPath: null, war: '**/*.war'
                
            }
        }
    }
}
