pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project with Maven.'
                echo 'Tool used: Maven'
                // Actual build command would go here, e.g., sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit.'
                echo 'Tools used: JUnit'
                // Actual test command would go here, e.g., sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube.'
                echo 'Tool used: SonarQube'
                // Actual code analysis command would go here, e.g., sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP.'
                echo 'Tool used: OWASP ZAP'
                // Actual security scan command would go here, e.g., sh 'zap-cli start'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to AWS EC2 staging environment.'
                echo 'Deployment tool: AWS CLI or Jenkins EC2 plugin'
                // Actual deployment command would go here, e.g., sh 'aws s3 cp ...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment.'
                echo 'Tools used: Selenium or similar'
                // Actual integration testing command would go here, e.g., sh 'selenium...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment.'
                echo 'This should be done with caution and potentially additional approval steps.'
                // Actual deployment command would go here, e.g., sh 'aws s3 cp ...'
            }
        }
    }
    post {
        always {
            echo 'This is a post-build step that always runs.'
        }
        success {
            echo 'Build was successful!'
        }
        failure {
            echo 'Build failed. Check the logs for details.'
        }
    }
}
