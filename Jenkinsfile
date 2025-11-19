pipeline {
    agent {
        docker {
            image 'maven:3.8.8-eclipse-temurin-11'
			args '-v $WORKSPACE/settings.xml:/root/.m2/settings.xml'
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
