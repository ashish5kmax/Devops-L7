pipeline {
    agent any

    environment {
        // Replace with your SonarQube installation name
        SONARQUBE_SERVER = 'SonarQube' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Pull code from your repository
                git 'https://github.com/your-repo/hello-world.git'
            }
        }

        stage('Static Code Analysis with SonarQube') {
            steps {
                script {
                    // Run SonarQube analysis
                    withSonarQubeEnv("${SONARQUBE_SERVER}") {
                        sh '''
                        sonar-scanner
                        '''
                    }
                }
            }
        }

        stage('Build and Run') {
            steps {
                // Execute the Python script
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
