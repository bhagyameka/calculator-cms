@Library('cmsdevopscorelib')_
/* if ("$buildordeploy" == 'build'){
 if ("$branch_name" == 'develop'){ 
 build "$branch_name"
 }
 else
 {
 echo "__________Build not allowed on $branch_name ____________"
   }
}
else
{
 if ("$branch_name" == 'develop'){ 
 deploy "$branch_name"
 }
 else
 {
 echo "__________deployment to $branch_name ENV is not allowed____________"
   }
 
} */
/* @Library('cmsdevopscorelib')_
if ("$buildordeploy" == 'build'){
  build "$branch_name"
 }
 else
 {
  deploy "$branch_name"
 } */

if ("$buildordeploy" == 'build'){
pipeline {
	environment {
			BN = "${branch_name}"
		}
		agent {label 'slave2'}
		stages {
			stage('Source Code from SCM') {
				steps {
					echo "You have chosen branch:"
	                                println "$BN"
					script{
											if ("$BN" == 'develop'){
					buildApp.SourcecodeCheckout("$BN")
						}
						else{
							echo " Build on $BN branch is not allowed"
							sh 'exit 1'
						}
				}
			}
			}
	stage('build using maven') {
				steps {
					
					echo "building using maven"
						script{
			    buildApp.maven()
					}
					}	
			}
			stage('unit testing') {
                               steps {
                                script{
                                 buildApp.unitTesting()
                                     }
                               }
   }
stage ('Test using CheckMarX') {
   
    steps {
        echo '*******CheckMarX start*******'
        
   
        echo '*******CheckMarX end*******'
    }
   
}


stage ('Upload to Jfrog') {
     steps {
         echo '*******upload to JFrog start*******'
      
         echo '*******upload to JFrog End*******'
     }
     }
		}
}
}
else 
{
 pipeline {
	environment {
			BN = "${branch_name}"
		}
		agent {label 'slave2'}
		stages {
			stage('Download from jfrog repository') {
				steps {
					echo "You have chosen branch:"
	                                println "$BN"
					script{
					 if ("$BN" == 'develop'){
				deployApp.downloadFromJfrog()
						}
						else{
							echo " Deployment on $BN branch is not allowed"
							sh 'exit 1'
						}
				}
			}
			}
	stage('Deploy on Weblogic') {
				steps {
					
					echo "Deployment"
						script{
			   deployApp.deploy("$BN")
					}
					}	
			}
			
		}
		
	}

}
