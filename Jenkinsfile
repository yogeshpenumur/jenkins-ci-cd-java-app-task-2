pipeline {
    agent none

    stages {
        stage('Clone Repository') {
            agent any
            steps {
                echo ' Cloning the repository...'
                git 'https://github.com/yogeshpenumur/jenkins-ci-cd-java-app-task-2'
            }
        }

        stage('Build') {
            agent any
            steps {
                echo '🏗 Building the project using Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            agent any
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            agent any
            steps {
                echo '🚀 Deploying the application (simulated)...'
                // Dummy deploy step — replace with actual deployment if needed
                sh 'echo "Deploying application to local server or environment..."'
            }
        }
    }
}
