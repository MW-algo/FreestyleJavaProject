pipeline {
    agent any
    tools {
        jdk  'jdk_17'
        maven 'mvn_3-9-7'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MW-algo/FreestyleJavaProject'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }

    }

    post {
        success {
            echo 'Build was successful'
        }

        failure {
            echo 'Build failed'
        }
    }


}