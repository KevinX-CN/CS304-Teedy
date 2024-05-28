pipeline {
	agent any
	stages {
		stage('build') { 
			steps {
 				sh 'mvn -B -DskipTests clean package' 
			}
		}
	 	stage('k8s') {
	 		steps {
	 			sh 'kubectl set image deployments/hello-node docs=6kevinx9/teedy_local:v1.0'
	 		}
	 	}
	}
	
	
}
