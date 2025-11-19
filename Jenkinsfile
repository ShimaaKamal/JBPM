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
				sh  'echo "Inside Docker container:"'
                sh  'echo "NEXUS_USER=$NEXUS_USER"'
            }
        }

		 stage('Publish to Nexus') {
            steps {
                configFileProvider([configFile(fileId: 'maven-settings', variable: 'MAVEN_SETTINGS')]) {
                   sh "mvn -s \"$MAVEN_SETTINGS\" -B deploy -DskipTests"
                }
            }
        }
    }
}
