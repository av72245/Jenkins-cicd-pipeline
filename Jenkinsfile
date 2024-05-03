pipeline {
    agent any
    environment {
        MAVEN_HOME = '/path/to/maven'
        PATH = "${env.PATH}:${env.MAVEN_HOME}/bin"
    }

    stages {
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
                    sh 'mvn dependency-check:check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    sh './deploy-staging.sh'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    sh 'selenium-tests.sh'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    sh './deploy-production.sh'
                }
            }
        }
    }
    post {
        always {
            mail to: 'your.email@example.com',
                 subject: "Jenkins Pipeline Stage ${currentBuild.currentResult}",
                 body: "A stage in the Jenkins Pipeline has completed. Check the logs for details."
        }
    }
}
