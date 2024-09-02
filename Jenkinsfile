pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                    // Example: Maven build
                    sh 'mvn clean package'
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running Unit and Integration Tests...'
                    // Example: Run unit tests using JUnit
                    sh 'mvn test'
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing the code...'
                    // Example: Run code analysis using SonarQube
                    sh 'sonar-scanner'
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                script {
                    echo 'Performing security scan...'
                    // Example: Run security scan using OWASP Dependency Check
                    sh 'dependency-check.sh --project myapp'
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to Staging...'
                    // Example: Deploy to AWS EC2 instance
                    sh 'aws deploy ...'
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    // Example: Run integration tests on staging environment
                    sh 'mvn verify -Pstaging'
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to Production...'
                    // Example: Deploy to AWS EC2 instance
                    sh 'aws deploy ...'
                }
            }
        }
    }
    
    post {
        always {
            emailext (
                to: 'developer@example.com',
                subject: "Pipeline: ${currentBuild.fullDisplayName}",
                body: """Pipeline ${currentBuild.fullDisplayName} finished with status: ${currentBuild.currentResult}.
                         Check Jenkins console output for more information.""",
                attachLog: true
            )
        }
    }
}
