pipeline {
    agent {
        docker {
            image 'maven:3.5-jdk-11'
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
