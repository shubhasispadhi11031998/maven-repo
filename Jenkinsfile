pipeline {
      agent any
	  tools {
	        maven 'Maven'
			
	  }
      stages{
             stage('Build'){
                     steps{
                              sh script: 'mvn clean package'
                      }

                } 
             stage('Upload war to nexus'){
                     steps{
						 script{
                              def mavenPom = readMavenPom file: 'pom.xml'
                              nexusArtifactUploader artifacts: [
							         [
									      artifactId: 'samplesnap',
										  classifier: '',
										  file: "/var/lib/jenkins/workspace/sampletest/target/samplesnap-${mavenPom.version}.war",
										  type: 'war'
								    ]
							], 
							credentialsId: '91b4626f-4b03-46dd-90b4-49bd67fcc344',
							groupId: 'com.jdevs',
							nexusUrl: '13.126.44.9:8081',
							nexusVersion: 'nexus3',
							protocol: 'http',
							repository: 'samplesnap',
							version: "${mavenPom.version}"
						 }
							}
                    }
         }
}		 
