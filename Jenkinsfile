pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Example: sh 'npm install' or mvn clean install
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: sh 'npm test' or mvn test
            }
            post {
                success {
                    emailext(
                        to: 'drishyasood700@gmail.com',
                        subject: "SUCCESS: Test Stage - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "The Test stage completed successfully.\n\nLogs are attached.",
                        attachmentsPattern: '**/*.log'
                    )
                }
                failure {
                    emailext(
                        to: 'drishyasood700@gmail.com',
                        subject: "FAILURE: Test Stage - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "The Test stage FAILED.\n\nLogs are attached.",
                        attachmentsPattern: '**/*.log'
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // Example: sh 'npm audit --json > scan.log'
            }
            post {
                success {
                    emailext(
                        to: 'drishyasood700@gmail.com',
                        subject: "SUCCESS: Security Scan - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "The Security Scan completed successfully.\n\nLogs attached.",
                        attachmentsPattern: '**/*.log'
                    )
                }
                failure {
                    emailext(
                        to: 'drishyasood700@gmail.com',
                        subject: "FAILURE: Security Scan - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "The Security Scan FAILED.\n\nLogs attached.",
                        attachmentsPattern: '**/*.log'
                    )
                }
            }
        }
    }
}

