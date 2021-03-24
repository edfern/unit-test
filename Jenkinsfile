pipeline{
	agent any 
	stages{
		stage('Compilar'){ 
			steps { 
				script {
					sh 'pwd'
					sh 'mvn package'
				}
				echo 'Compilacion finalizada exitosamente'
			} 
		}
		stage('Analisis'){
			steps{
				script{
					scannerHome = tool 'sonarQubeScanner'
				}
				withSonarQubeEnv('sonaServer'){
					sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=test-2-sonar -Dsonar.projectVersion=1.0 -Dsonar.sources=./src -Dsonar.java.binaries=./target/classes -Dsonar.login=ab83ea97c8f73064f0e996794e3b34b0ab7fc42b"
				}
			}
		}
	}
}
