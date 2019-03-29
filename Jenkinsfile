pipeline {
    agent any

    tools {
        maven 'localMaven'
    }
    stages {
        stage('Init') {
            steps {
                sh 'mvn clean package'
            }

            post {
                success {
                    echo 'Now archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deploy to Staging') {
            steps {
                build job: 'deploy-to-staging'
            }
        }

        stage ('Deploy to Production') {
            steps {
                timeout(time:5, unit:'DAYS') {
                    input message: 'Approve PRODUCTION Deployment?'
                }

                post {
                    success {
                        echo 'Code deployed to Production'
                    }

                    failure {
                        echo 'Deployment failed'
                    }
                }
            }
        }
    }
}