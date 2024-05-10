pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project with Maven.'
                echo 'Tool used: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit.'
                echo 'Tools used: JUnit'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality with SonarQube.'
                echo 'Tool used: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP.'
                echo 'Tool used: OWASP ZAP'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to AWS EC2 staging environment.'
                echo 'Deployment tool: AWS CLI or Jenkins EC2 plugin'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment.'
                echo 'Tools used: Selenium or similar'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment.'
                echo 'This should be done with caution and potentially additional approval steps.'
            }
        }
    }
    post {
        always {
            emailext(
                subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' - ${currentBuild.currentResult}",
                body: "Please see the attached log for more details.",
                to: 'example@email.com',
                attachmentsPattern: '**/logs/*.log'
            )
        }
    
   success {
    echo 'Build was successful!'
    emailext(
        to: 'av72245@gmail.com',
        subject: "Build ${env.BUILD_NUMBER} Successful",
        body: "Great news! The build was successful. Check Jenkins for more details.",
        attachmentsPattern: '**/logs/*.log'
    )
}
failure {
    echo 'Build failed. Check the logs for details.'
    emailext(
        to: 'av72245@gmail.com',
        subject: "Build ${env.BUILD_NUMBER} Failed",
        body: "Alert: The build failed. Check Jenkins for more details.",
        attachmentsPattern: '**/logs/*.log'
    )
}

}

}
