pipeline {
    agent any

    environment {
        SONARQUBE_SERVER = 'SonarQube'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ashish5kmax/Devops-L7.git',
                    credentialsId: 'c72da4aa-0d6d-4d81-8090-662cd3608051' // Use the credentials ID
            }
        }

        stage('Static Code Analysis with SonarQube') {
            steps {
                script {
                    withSonarQubeEnv("${SONARQUBE_SERVER}") {
                        sh 'sonar-scanner'
                    }
                }
            }
        }

        stage('Build and Run') {
            steps {
                sh 'python3 hello_world.py'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
