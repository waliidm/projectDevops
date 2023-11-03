pipeline {
    agent any

    environment {
        dockerhubregistry = "walidmehrez/walid_projectdevops"
        registryCredential = 'dockerhub'
        dockerImage = ''
     }

    stages {        

         // building backend
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        // Running Unit Tests
        stage('Run Unit Tests') {
            steps {
                sh 'mvn test'
            }
        }

        // SonarQube Analysis
        stage('SonarQube Analysis') {
                steps {
                    withSonarQubeEnv('Sonar') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        // Nexus Deployment
        stage('Deploy to Nexus') {
                steps {
                        sh 'mvn deploy'
                }
            }
        
        // Building Docker images
        stage('Building image') {
        steps{
            script {
            dockerImage = docker.build(dockerhubregistry,".")
            }
        }
        }

          // Uploading Docker image into Docker Hub
        stage('Upload Image') {
        steps{    
            script {
                docker.withRegistry( '', registryCredential ) {
                dockerImage.push()
                }
            }
        }
        }
	
    }
}
