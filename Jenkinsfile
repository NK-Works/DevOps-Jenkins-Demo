pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/NK-Works/DevOps-Jenkins-Demo.git' 
                echo 'Building the code using npm...'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests...'
                echo 'Running integration tests...'
            }
            post {
                always {
                    emailext subject: "Pipeline '${currentBuild.fullDisplayName}' - Tests Completed",
                              body: 'Unit and integration tests have completed.',
                              to: 'anneshu123@gmail.com',
                              attachLog: true
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                echo 'Running code analysis using SonarQube...'
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP ZAP...'
            }
            post {
                always {
                    emailext subject: "Pipeline '${currentBuild.fullDisplayName}' - Security Scan Completed",
                              body: 'Security scan has completed.',
                              to: 'anneshu123@gmail.com',
                              attachLog: true
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to staging server (e.g., Netlify instance)...'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to production server (e.g., AWS EC2 instance)...'
            }
        }
    }
    post {
        success {
            emailext subject: "Pipeline '${currentBuild.fullDisplayName}' Successful",
                      body: 'The build was successful. Congratulations!',
                      to: 'anneshu123@gmail.com',
                      attachLog: true
        }
        failure {
            emailext subject: "Pipeline '${currentBuild.fullDisplayName}' Failed",
                      body: 'The build has failed. Please check console log file.',
                      to: 'anneshu123@gmail.com',
                      attachLog: true
        }
    }
}
