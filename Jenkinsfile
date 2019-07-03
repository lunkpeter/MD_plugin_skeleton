// Tell Jenkins how to build projects from this repository
pipeline {
	
	agent {
		label 'magicdraw19'
	}
	
	// Keep only the last 5 builds
	options {
		buildDiscarder(logRotator(numToKeepStr: '5'))
	}
	
	tools { 
		jdk 'Oracle JDK 8' 
	}

	stages { 
		stage('Build Plug-in') { 
			steps {
				sh 'rm -rf build/dependency-cache'
				sh './gradlew clean'
				sh './gradlew build publish'
			}
		}
	}

	post {
		always {
			archiveArtifacts artifacts: 'com.incquerylabs.magicdraw.plugin.example/build/distributions/com.incquerylabs.magicdraw.plugin.example-*.zip', onlyIfSuccessful: true
		}
	}
}