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

        stage('Run') {
			steps{
				echo "Run image"
				sh returnStdout: true, script: "docker run --rm -d --name ${JOB_NAME} -p 8081:5000 ${img}"
			}
		}
		
          
      
    }
}