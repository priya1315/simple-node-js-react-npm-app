pipeline {
    agent {
        docker {
            image 'node:20.9.0-alpine3.18' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('Dependency-Check') {
            steps {
                dependencyCheck additionalArguments: ''' 
                    -o './'
                    -s './'
                    -f 'ALL' 
                    --prettyPrint''', odcInstallation: 'Dependency-Check'
        
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
        stage('Debug') {
    steps {
        sh 'ls -la'
    }
    }
    }
   
}