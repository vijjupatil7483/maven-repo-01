pipeline {
    // add your slave label name
    agent { label 'jenkins-slave-node'}
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
	      sshagent(['devopsadmin']) {
              sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war  devopsadmin@54.147.152.43:/opt/tomcat9/webapps"
	      }
         }
        }
        
    }
}
