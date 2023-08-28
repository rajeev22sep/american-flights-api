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
				bat "mvn test"
			}
		}

		stage('Deploy Sandbox') {
			
			steps {
				bat 'mvn -U -V -e -B  -DskipTests deploy -Pch-sandbox -DmuleDeploy' 
				
			}
		}

		stage('Deploy Design') {
			
			steps {
				bat 'mvn -U -V -e -B  -DskipTests deploy -Pch-design -DmuleDeploy'
			}
		}
	}
}
