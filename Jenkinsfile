pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Example build step using Maven
                    echo 'Building the code...'
                    sh 'mvn clean package'
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    // Example test step using JUnit and integration tests
                    echo 'Running unit and integration tests...'
                    sh 'mvn test'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    // Example code analysis using SonarQube
                    echo 'Performing code analysis...'
                    sh 'mvn sonar:sonar'
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    // Example security scan using OWASP Dependency-Check
                    echo 'Performing security scan...'
                    sh 'dependency-check.sh --project MyProject --scan ./'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    // Example deployment step to AWS EC2
                    echo 'Deploying to staging...'
                    sh 'deploy-staging.sh'
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    // Example integration tests on staging environment
                    echo 'Running integration tests on staging...'
                    sh 'integration-tests.sh'
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    // Example deployment step to production
                    echo 'Deploying to production...'
                    sh 'deploy-production.sh'
                }
            }
        }
    }
    post {
        always {
            script {
                // Send email notifications (configure SMTP settings in Jenkins)
                echo 'Sending notification email...'
                emailext(
                    subject: "Build ${currentBuild.fullDisplayName} - ${currentBuild.result}",
                    body: "Build ${currentBuild.fullDisplayName} finished with status: ${currentBuild.result}\n\nCheck the build logs for details.",
                    to: 'viloshanaravindu@gmail.com',
                    attachLog: true
                )
            }
        }
    }
}
