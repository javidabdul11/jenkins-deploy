pipeline {
	agent any
   stages {
    	stage('Build Application') {
    		steps {
    			echo 'Build Application....'
    				bat 'mvn -f ".\\jenkins-deploy\\pom.xml" clean install'
    			}
    		}
    			stage('Test') {
    		   steps {
    		   		echo 'Test Application...'
    		   		bat 'mvn -f ".\\jenkins-deploy\\pom.xml" test'
    		   	}
    		  }
    		  
    		  	stage('Deploy CloudHub') { 
        
				  steps {
				    echo 'Deploying only because of code commit...'
				    echo 'Deploying to  dev environment....'
				    bat 'mvn -f ".\\jenkins-deploy\\pom.xml" package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -DworkerType=Micro -Dworkers=1 -Dregion=us-west-2'
				  }
				  
				}
   		}
   }
