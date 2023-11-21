pipeline {
    agent any 
	environment {
		def scannerHome = tool 'Sonar-scanner';
		
		
	
	}
    stages {
	  stage('SCM') {
		  steps {
		    checkout scm
		  }
	  }
	    
	
stages {
        stage('GitGuardian Scan') {
            agent {
                docker { image 'gitguardian/ggshield:latest' }
            }
            environment {
                GITGUARDIAN_API_KEY = credentials('gitguardian-api-key')
            }
            steps {
                sh 'ggshield secret scan ci'
            }
        }
    }	      
	    


	  

	  stage('SAST Analysis-SonarQube') {
		  steps {
		    withSonarQubeEnv('SonarQube') {
		      sh "${scannerHome}/bin/sonar-scanner"
	    }
	    }
	  }


    
	    
	  stage ("Dynamic Analysis - OWASP ZAP") {
		  steps {
		  	sh "docker run -t owasp/zap2docker-stable zap-baseline.py -t https://aopartnersdev.com.ng/devsecops/ || true"
		 	 }
			}
	    

	    

	    

	
	
	

	
    

        

    }
}
