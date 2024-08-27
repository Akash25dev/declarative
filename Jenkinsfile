pipeline{
   agent any
             parameters {
               choice choices: ['QA', 'UAT', 'DEV'], name: 'ENVIRONMENT'
             }
             stages {
	    stage('Checkout') {
	        steps {
			checkout scm			       
		      }}
		stage('Build') {
	           steps {
			  sh 'mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( "${env.ENVIRONMENT}" == 'QA' ){
        	sh 'cp target/declarative.war /home/akash/Documents/Maven/apache-tomcat-9.0.93/webapps'
        	echo "deployment has been done on QA!"
			 }
			elif ( "${env.ENVIRONMENT}" == 'UAT' ){
    		sh 'cp target/declarative.war /home/akash/Documents/Maven/apache-tomcat-9.0.93/webapps'
    		echo "deployment has been done on UAT!"
			}
			echo "deployment has been done!"
			fi
			
			}}}
	   }
}

