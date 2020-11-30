pipeline 
      {
      environment
		{
		//registry = "rupsdan/webapp3"
		//registryCredential = "dockerHub"
		docker.withRegistry('https://registry.hub.docker.com', 'dockerHub') 
		}
      agent any
      	stages {
      	      stage("Cloning Git by RD")
      	      		{
      	      		steps 
      	      			{
					git branch: 'main',
                credentialsId: 'dockerHub',
                url: 'ssh://git@github.com:rupam88/docker2.git'
					

 				 //git url: 'https://github.com/rupam88/docker2.git'
       	    			}
      	    		}
      	    
      	      stage("Building Image by RD")
      	          {
      	          steps 
      	              {
      	              script
      	                  {
      	               docker.build registry + ":$BUILD_NUMBER"
      	                   }
      	               }
      	            }
      	         stage("Deploy Image")
      	            {
      	            steps
      	               {
      	                script
      	                   {
      	                   docker.withRegistry( '', registryCredential) 
      	                      {
      	                      dockerImage.push()
      	                      }
      	                    }
		 	  }
	      	       }  	
	      	  }
	      	  }     
