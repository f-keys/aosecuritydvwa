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
	    
	
	    
	    
	    


	  

	  stage('SAST Analysis-SonarQube') {
		  steps {
		    withSonarQubeEnv('SonarQube') {
		      sh "${scannerHome}/bin/sonar-scanner"
	    }
	    }
	  }


    
	    
	 
	    

	    

	    

	
	
	

	
    

        

    }
}
