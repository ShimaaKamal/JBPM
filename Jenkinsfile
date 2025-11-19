pipeline {
    agent {
        docker {
            image 'maven:3.8.8-eclipse-temurin-11'
        }
    }

	environment {
        NEXUS_USER = credentials('nexus-username')
        NEXUS_PASS = credentials('nexus-password')
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn -version'
				sh 'mvn clean install'
            }
        }

		 stage('Publish to Nexus') {
            steps {
                sh "mvn -B deploy -DskipTests"
            }
        }
    }
}
