pipeline {
    agent {
        docker {
            image 'node:20.9.0-alpine3.18' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stages {
		stage('Checkout SCM') {
			steps {
				git url: 'https://github.com/minXnub/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP Dependency-Check') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
   
}