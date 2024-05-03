pipeline {
    agent any
    tools {
        maven 'default maven'
    }
    environment {
        PATH = "/opt/homebrew/opt/maven/bin:${env.PATH}"
    }
    stages {
        stage('Initialization') {
            steps {
                script {
                    sh 'mvn -version'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    sh 'mvn org.owasp:dependency-check-maven:check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    sh 'mvn deploy'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    sh 'mvn verify'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    sh 'mvn deploy -Pproduction'
                }
            }
        }
    }
    post {
        always {
            mail to: 'your.email@example.com',
                 subject: "Build ${env.BUILD_NUMBER} Completed",
                 body: "The build of ${env.JOB_NAME} ${env.BUILD_NUMBER} completed."
        }
        success {
            echo "Build was successful!"
            // Additional success actions here
        }
        failure {
            echo "Build failed."
            // Additional failure actions here
        }
    }
}
