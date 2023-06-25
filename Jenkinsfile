pipeline {
    agent any
   
	environment {
		registry = "snehalhhande/CICDJenkins"
		img = "$registry" + ":${env.BUILD_ID}"
		//registryCredential = 'docker-hub-login' 
    }	

    stages {
        stage('Checkout') {
            steps {
                git branch: 'dotnetwebapp', url: 'https://github.com/snehalhhande/CICDJenkins.git'
                sh 'ls -la'
            }
        }
		stage('Stop running Container') {
			steps{
					sh returnStatus: true, script: 'docker stop $(docker ps -a | grep ${JOB_NAME} | awk \'{print $1}\')'
					sh returnStatus: true, script: 'docker rmi $(docker images | grep ${registry} | awk \'{print $3}\') --force' 
					sh returnStatus: true, script: 'docker rm ${JOB_NAME}'
				}	
		}
        stage('Build') {
            steps {
				echo "Building our image"
				script {
					dockerImg = docker.build("${img}")
                }
            }
        }
		
          
      
    }
}