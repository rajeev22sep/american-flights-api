pipeline {
	agent any
	
	environment {
		ANYPOINT_CREDS = credentials('ANYPOINT_CREDENTIAL')
	}
	

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
		
		environment {
				CLIENT_ID = credentials('SANDBOX_CLIENT_ID')
				CLIENT_SECRET = credentials('SANDBOX_CLIENT_SECRET')
	}
	
			
			steps {
				bat 'mvn -U -V -e -B  -DskipTests deploy -Pch-sandbox -DmuleDeploy -Dcloudhub.userName="%ANYPOINT_CREDS_USR%" -Dcloudhub.password="%ANYPOINT_CREDS_PSW%" -Dsandbox.clientId="%CLIENT_ID%" -Dsandbox.clientSecret="%CLIENT_SECRET%" ' 
				
			}
		}

		
	}
}
