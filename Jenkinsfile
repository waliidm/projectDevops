pipeline {
    agent any

    stages {
        
        stage('Test') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Build') {
            steps {
                // Build your Maven project
                sh 'mvn clean package'
            }
        }
        
        stage('Run Unit Tests') {
            steps {
                // Execute unit tests
                sh 'mvn test'
            }
        }
    }
}
