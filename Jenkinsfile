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
	 			sh 'kubectl set image deployments/hello-node docs=6d276671bc6e'
	 		}
	 	}
	}
	
	post {
 		always {
 			archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
 			archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
 			archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
 		}
	}
}
