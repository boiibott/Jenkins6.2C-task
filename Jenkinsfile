pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Maven: Java build automation with dependency management and convention-over-configuration.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'JUnit will validate individual units of code,'
                echo 'To test the integration of application components, use Selenium WebDriver.'
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
                echo 'In order to make sure the source complies with industry standards, SonarQube will examine it and find errors, vulnerabilities'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'The codebase will undergo a security scan by OWASP ZAP, which will find known security flaws or possible vulnerabilities such security errors in configuration.'
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
