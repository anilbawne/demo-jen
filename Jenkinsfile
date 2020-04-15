pipeline {
  agent any
        options {
        timeout(time: 5, unit: 'SECONDS') 
    }
    
  stages {
    stage('Build Application') { 
      steps {
        bat 'mvn clean install'
      }
    }
 	stage('Test') { 
      steps {
        echo 'Test Appplication...' 
      }
    }
 	
    stage('Deploy CloudHub') { 
    	      environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
       steps {
        echo 'Deploying only because of code commit...'
        bat 'mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Denvironment=Sandbox'
      }
    }
  }
}