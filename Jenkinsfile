pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests...'
                echo 'Running integration tests...'
            }
            post {
                success {
                    emailNotification("Unit and Integration Tests", "Success")
                }
                failure {
                    emailNotification("Unit and Integration Tests", "Failure")
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
            }
            post {
                success {
                    emailNotification("Security Scan", "Success")
                }
                failure {
                    emailNotification("Security Scan", "Failure")
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
            }
        }
    }
}

def emailNotification(stageName, status) {
    emailext (
        to: 'yashmit4863.be22@chitkara.edu.in',
        subject: "Pipeline ${status} - ${stageName}",
        body: "The ${stageName} stage has ${status}. Please review the logs attached.",
        attachLog: true
    )
}
