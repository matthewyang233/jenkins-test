pipeline {
    agent any
<<<<<<< HEAD

    tools {
        maven 'localMaven'
    }
=======
    
    tools {
        maven 'localMaven'
    }
    
>>>>>>> 06e1f3ba49fd451c205e60f8c31c0cbbeeb6fe6c
    stages {
        stage('Build') {
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
<<<<<<< HEAD

=======
        
>>>>>>> 06e1f3ba49fd451c205e60f8c31c0cbbeeb6fe6c
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

                build job: 'deploy-to-prod'
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
