// pipeline {
// 	agent any
// 	stages {
// 		stage('Checkout SCM') {
// 			steps {
// 				git url: 'https://github.com/minXnub/JenkinsDependencyCheckTest.git'
// 			}
// 		}

// 		stage('OWASP Dependency-Check') {
// 			steps {
// 				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check'
// 			}
// 		}
// 	}	
// 	post {
// 		success {
// 			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
// 		}
// 	}
// }
pipeline {
	agent {
		docker {
			image 'composer:latest'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'composer install'
			}
		}
		stage('Test') {
			steps {
                sh './vendor/bin/phpunit tests'
            }
		}
	}
}