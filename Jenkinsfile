pipeline {
	agent any
	

	stages {
		stage('Build') {
			steps {
				bat 'mvn -B -U -e -V clean -DskipTests package'
			}
		}

		stage('Test') {
			steps {
				bat "mvn -DskipTests test"
			}
		}

		stage('Deploy Sandbox') {
			
			steps {
				bat 'mvn -U -V -e -B  -DskipTests deploy -Pch-sandbox -DmuleDeploy' 
				
			}
		}

		
	}
}
