pipeline {
    agent any 
	environment {
		def scannerHome = tool 'Sonar-scanner';
		GITGUARDIAN_API_KEY = credentials('C9c29b0Bad94a3c2dACac7E3bDe31cb3feC10806fBEaAa709Dcb4476D94F2fEC6bD8A0F')
		
	
	}
    stages {
	  stage('SCM') {
		  steps {
		    checkout scm
		  }
	  }
	    
	
	             stage('Secrets Management-GitGuardian Scan') {
            agent {
                docker { image 'gitguardian/ggshield:latest'
		       args '-i --entrypoint='}
            }
            steps {
                sh 'ggshield secret scan ci'
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
