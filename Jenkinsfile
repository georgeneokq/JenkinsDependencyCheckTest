pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git url:'https://github.com/georgeneokq/JenkinsDependencyCheckTest.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default', nvdCredentialsId: 'nvd_api_key'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}