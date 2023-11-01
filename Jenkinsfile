pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                    script {
                        git branch: 'main', credentialsId: '5419e81b-9ddf-417e-8e6c-5b0037bfe730', url: 'https://github.com/waliidm/projectDevops'
                    }
                } 
        }
        
        stage('git') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
