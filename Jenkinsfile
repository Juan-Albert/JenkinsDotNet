pipeline {
	agent any
	environment {
        dotnet = 'C:\\"Program Files"\\dotnet\\dotnet.exe'
    }
	stages {
		stage('Checkout') {
			steps {
			    cleanWs()
				bat "git clone https://github.com/Juan-Albert/JenkinsDotNet.git ."
			}
		}
		
		stage('Restore') {
            steps {
                bat "%dotnet% restore"
            }
        }
		
		stage('Test') {
            steps {
                bat "%dotnet% test --configuration Release --no-build --logger trx --results-directory TestResults"
            }
        }
        
        stage('Build') {
            steps {
                bat "%dotnet% build --configuration Release --no-restore"
            }
        }
        
        stage('Publish') {
            steps {
                bat """
                    %dotnet% publish --configuration Release --no-build --output "Publish" --framework net6.0
                """
                archiveArtifacts artifacts: 'Publish/*/', fingerprint: true
            }
        }
	}
}