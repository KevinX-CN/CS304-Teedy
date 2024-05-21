pipeline {
	agent any
	stages {
		stage('build') { 
			steps {
 				sh 'mvn -B -DskipTests clean package' 
			}
		}
 		stage('build image') {
 			steps {
 				sh 'docker build -t teedy2024_manual .'
 			}
 		}
 		stage('upload image') {
 			steps {
 				sh 'docker tag teedy2024_manual 6kevinx9/teedy_local:v1.0'
 				sh 'docker push 6kevinx9/teedy_local:v1.0'
 			}
 		}
 		stage('run image') {
 			steps {
 				sh 'docker run -d -p 8084:8080 --name teedy_manual01 teedy2024_manual'
				sh 'docker run -d -p 8082:8080 --name teedy_manual02 teedy2024_manual'
				sh 'docker run -d -p 8083:8080 --name teedy_manual03 teedy2024_manual'
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
