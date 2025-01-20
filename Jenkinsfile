pipeline {
    // add your slave label name
    agent { label 'my-first-jenkins-slave-server'}
    tools{
        maven 'maven-test'
    }
    stages {
        stage ('Checkout_SCM') {

            steps {
          	    
	     checkout scm
            }
        }

        stage ('Maven_Build') {

            steps {
               sh 'mvn clean package'
            }
        }
        
        stage ('Deploy_Tomcat') {

            steps {
	      sshagent(['Tomcat-server-key']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@107.21.50.234:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}
