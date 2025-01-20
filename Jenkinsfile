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
	      sshagent(['My-Tomcat-server']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  ec2-user@3.82.37.97:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}
