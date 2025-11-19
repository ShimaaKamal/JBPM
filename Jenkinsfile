pipeline {
    agent {
        docker {
            image 'maven:3.8.8-eclipse-temurin-11'
        }
    }

    stages {
        stage('build') {
            steps {
                sh 'mvn -version'
				sh 'mvn clean install'
            }
        }
    }
}
