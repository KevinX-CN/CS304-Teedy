pipeline {
	agent any
	stages {
		stage('Build') { 
			steps {
 				sh 'mvn -B -DskipTests clean package' 
			}
		}
		stage('pmd') {
 			steps {
 				sh 'mvn pmd:pmd'
 			}
 		}
		stage('surefire-report') {
 			steps {
 				sh 'mvn surefire-report:report'
 			}
 		}
		stage('javadoc') {
 			steps {
 				sh 'mvn javadoc:javadoc --fail-never'
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
