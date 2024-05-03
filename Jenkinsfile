pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Tool: Maven
                    sh 'mvn clean install'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Tool: JUnit for unit testing, Mockito for integration
                    sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    // Tool: SonarQube
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    // Tool: OWASP Dependency Check
                    sh 'mvn dependency-check:check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    // Deployment to AWS EC2 via scripts or AWS CLI
                    sh './deploy-staging.sh'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    // Tool: Selenium for web apps
                    sh 'selenium-tests.sh'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    // Deployment to AWS EC2 via scripts or AWS CLI
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
