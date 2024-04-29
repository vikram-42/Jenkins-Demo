pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                 echo 'Use Maven to build the code'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Run unit and integration tests using Selenium and junit'
            }

            post {
                success {
                    echo 'Selenium and junit test successfully completed'
                    emailext(
                        to: 'rajvikram1998@gmail.com',
                        subject:"The status of the Unit and Integration Test:  ${currentBuild.result}",
                        body:'Check the log files to obtain additional information about the process',
                        attachLog: true
                    )
                }
                failure {
                    echo 'The Unit and Integration Testing failed'
                    emailext(
                        to: 'rajvikram1998@gmail.com',
                        subject:"The status of the Unit and Integration Test:  ${currentBuild.result}",
                        body:'Check the log files to obtain additional information about the process',
                        attachLog: true
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Integrate with SonarQube for code analysis'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Perform security scan using OWASP ZAP'
            }

            post {
                success {
                    echo 'OWASP ZAP Security Scanning successfully completed'
                    emailext(
                        to: 'rajvikram1998@gmail.com',
                        subject:"The status of the Security Scanning:  ${currentBuild.result}",
                        body:'Check the log files to obtain additional information about the process',
                        attachLog: true
                    )
                }

                failure {
                    echo 'OWASP ZAP Security Scanning failed'
                    emailext(
                        to: 'rajvikram1998@gmail.com',
                        subject:"The status of the Security Scanning:  ${currentBuild.result}",
                        body:'Check the log files to obtain additional information about the process',
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploy application to staging server using AWS CodeDeploy'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests on staging environment with Selenium'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploy application to production server using AWS CodeDeploy'
            }
        }
    }
}
