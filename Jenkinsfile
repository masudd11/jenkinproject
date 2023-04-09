pipeline {
    agent any
	tools {
		maven 'Maven'
	}         
	
    stages {
		stage('Test') {
		    steps {
			    echo "Testing..."
			    sh 'mvn test'
		    }
	    }
	    stage('Build') {
		    steps {
			    sh 'mvn clean package'
		    }
	    }
	    stage('Build Docker Image') {
		    steps {
			    sh 'whoami'
				sh 'pwd'
			    // sh 'docker build -t masudd11/helloworld:${BUILD_NUMBER} .'
				sh 'docker build -t khaledrepo/hellopro:${BUILD_NUMBER} .'
			}
		}
	    
	    stage("Push Docker Image") {
		    steps {
				// withDockerRegistry(credentialsId:'usernmepass'){
					// sh 'docker push masudd11/helloworld:${BUILD_NUMBER}'
		        withDockerRegistry(credentialsId: 'aws', url: 'https://ap-south-1.console.aws.amazon.com/ecr/repositories?region=ap-south-1') {
					sh 'docker push khaledrepo/hellopro:${BUILD_NUMBER}'   
				}
			}
		}
    }
}
