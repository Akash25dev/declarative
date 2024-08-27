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
			  sh '/home/swapnil/Documents/DevOps-Software/apache-maven-3.9.4/bin/mvn install'
	                 }}
		stage('Deployment'){
		    steps {
			script {
			 if ( "${env.ENVIRONMENT}" == 'QA' ){
        	sh 'cp target/CICD.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
        	echo "deployment has been done on QA!"
			 }
			elif ( "${env.ENVIRONMENT}" == 'UAT' ){
    		sh 'cp target/CICD.war /home/swapnil/Documents/DevOps-Software/apache-tomcat-9.0.79/webapps'
    		echo "deployment has been done on UAT!"
			}
			echo "deployment has been done!"
			fi
			
			}}}
	   }

         stages{
            stage(clone){
                   steps{
                     git 'https://github.com/Akash25dev/declarative.git'
                   }
            }
            stage(build){
                   steps{
                     sh 'mvn install'
                   }
            }
            stage(deploy){
                   steps{
                     sh 'cp target/declarative.war /home/akash/Documents/Maven/apache-tomcat-9.0.93/webapps'
                   }
            }
        }
}

