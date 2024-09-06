pipeline {
    agent any

    triggers {
        // Trigger the pipeline on new commits with a short delay
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using Maven..'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running tests using JUnit and TestNG...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Analyzing code using SonarQube...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Performing security scan using OWASP Dependency-Check...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying to AWS EC2 instance...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests using Selenium...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying to AWS EC2 instance...'
            }
        }
    }

    post {
        always {
            script {
                echo 'Sending notification emails...'
                emailext(
                    subject: "Pipeline ${env.JOB_NAME} - Build #${env.BUILD_NUMBER} - ${currentBuild.result}",
                    body: "The buid has finished successfully! Build URL: ${env.BUILD_URL}",
                    attachLog: true,
                    to: 'aero.golden7@gmail.com'
                )
            }
        }
    }
}
