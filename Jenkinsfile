pipeline {
	agent any
	
	stages {
		stage('Checkout') {
			steps {
			    cleanWs()
				bat "git clone https://github.com/Juan-Albert/JenkinsDotNet.git ."
			}
		}
	}
}