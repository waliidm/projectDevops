pipeline {
    agent any

    stages {        

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

	stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Sonar') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

	stage('Deploy to Nexus') {
            steps {
                    sh 'mvn deploy'
            }
        }
    }
}
