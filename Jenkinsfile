pipeline {
    agent any

    triggers {
        pollSCM('* * * * *') // Poll every minute; you can adjust as needed
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone source code from the repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build the project using Gradle
                sh './gradlew assemble'
            }
        }

        stage('Test') {
            steps {
                // Run tests using Gradle
                sh './gradlew test'
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
