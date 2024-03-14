pipeline {
    agent any
    
    stages {
        stage('Build Stage') {
            steps {
                echo 'Building the code using Maven...'
            }
        }
        
        stage('Unit and Integration Tests Stage') {
            steps {
                echo 'Running unit tests...'
                echo 'Running integration tests...'
            }
        }
        
        stage('Code Analysis Stage') {
            steps {
                echo 'Running code analysis using SonarQube...'
            }
        }
        
        stage('Security Scan Stage') {
            steps {
                echo 'Performing security scan using OWASP ZAP...'
            }
        }
        
        stage('Deploy to Staging Stage') {
            steps {
                echo 'Deploying the application to staging server (e.g., AWS EC2 instance)...'
            }
        }
        
        stage('Integration Tests on Staging Stage') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        
        stage('Deploy to Production Stage') {
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
                      body: 'The build has failed. Please check the logfile for more.',
                      to: 'anneshu123@gmail.com',
                      attachLog: true
        }
    }
}
