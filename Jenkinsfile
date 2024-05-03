pipeline {
    agent any
    tools {
        // Ensure this name matches the Maven configuration in your Jenkins Global Tool Configuration
        maven 'default maven'
    }
    environment {
        // Make sure Maven's bin directory is in the PATH
        PATH = "/opt/homebrew/opt/maven/bin:${env.PATH}"
    }
    stages {
        stage('Initialization') {
            steps {
                script {
                    // This step is just for debugging; it prints the Maven version to the console
                    sh 'mvn -version'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    // Performs clean and install Maven phases
                    sh 'mvn clean install'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Runs unit tests assuming they are configured in the pom.xml
                    sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    // Example: Integrating with SonarQube for code quality analysis
                    // Make sure SonarQube is configured in Maven settings
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    // Example: Running a dependency check for security vulnerabilities
                    sh 'mvn org.owasp:dependency-check-maven:check'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    // Example: Deploy to a staging server
                    // This will require additional configuration in your Maven pom.xml or scripts
                    sh 'mvn deploy'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    // Assuming integration tests are set up to run against the staging environment
                    sh 'mvn verify'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    // Deploy to production; this should include additional safeguards
                    sh 'mvn deploy -Pproduction'
                }
            }
        }
    }
    post {
        always {
            // Sending an email if configured or other cleanup steps
            mail to: 'your.email@example.com',
                 subject: "Build ${env.BUILD_NUMBER} Completed",
                 body: "The build of ${env.JOB_NAME} ${env.BUILD_NUMBER} completed."
            // Add any other post-build actions here
        }
        success {
            // Actions for a successful build
        }
        failure {
            // Actions for a failed build
        }
    }
}
