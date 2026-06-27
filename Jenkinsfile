pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run App (test only)') {
            steps {
                sh 'echo "Build success, ready to deploy"'
            }
        }
    }

    post {
        success {
            echo "✅ CI Pipeline SUCCESS"
        }
        failure {
            echo "❌ CI Pipeline FAILED"
        }
    }
}
