pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'npm is a tool for managing JavaScript packages and build tasks in web development projects.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Jest is a JavaScript testing framework by Facebook for unit tests. Cypress is for end-to-end tests on web apps.'
               
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
                echo 'With the use of ESLint, a JavaScript static code analysis tool, code patterns can be found to increase maintainability and quality.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'OWASP Dependency-Check finds weak points in project dependencies, looks for parts that might be compromised, and generates security alerts.'
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
                echo 'AWS CodeDeploy will automate the deployment of the application to a staging server like an AWS EC2 instance.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Postman will conduct integration tests on the staging environment to ensure the application functions properly in a production-like setting.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Utilize an additional AWS EC2 instance or AWS CodeDeploy to automate the applications deployment to a production server.'
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
