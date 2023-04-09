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
			    sh 'docker build -t masudd11/helloworld:${BUILD_NUMBER} .'
			}
		}
	    
	    stage("Push Docker Image") {
		    steps {
				sh 'pwd'
				sh 'docker image tag masudd11/helloworld:${BUILD_NUMBER} masudd11/helloworld:1'
				sh 'docker push masudd11/helloworld:1'
				
			}

		}
    }
}
