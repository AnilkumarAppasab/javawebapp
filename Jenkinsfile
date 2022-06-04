pipeline {
  agent {
      label 'maven' 
}
environment {
       NEXUS_VERSION = "nexus3"
       NEXUS_PROTOCOL = "http"
       NEXUS_URL = "3.109.209.246:8081"
       NEXUS_REPOSITORY = "pipeline-mvn"
       NEXUS_CREDENTIAL_ID = "NEXUS_CRED"
}
stages{
	  stage ('Build'){
	    steps{
		sh '''
			mvn clean package
			'''
		}
	  }
 stage("sonarqube"){
  steps{
     withSonarQubeEnv('sonarqube'){
	     sh "mvn sonar:sonar"
     }
  }
 }
	
}
}
