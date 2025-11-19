pipeline {
    agent {
        docker {
            image 'maven:3.5.4-jdk-11.0.28'
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
