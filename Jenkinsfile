pipeline {
    agent any
   
	environment {
		registry = "snehalhhande/cicdjenkins"
		img = "$registry" + ":${env.BUILD_ID}"
		//registryCredential = 'docker-hub-login' 
    }	

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/snehalhhande/cicdjenkins.git'
                sh 'ls -la'
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