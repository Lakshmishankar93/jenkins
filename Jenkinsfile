pipeline {
    agent any
    stages {
        stage('nginx installation') {
            steps {
                script {
                    // Install nginx
                    sh 'sudo yum install nginx -y'
                    // Start nginx service
                    sh 'sudo service nginx start'
                }
            }
        }
        stage('copying the path') {
            steps {
                script {
                    // Copy index.html to nginx HTML directory
                    sh 'sudo cp -r /var/lib/jenkins/workspace/pipeabi/index.html /usr/share/nginx/html/'
                    // Restart nginx service
                    sh 'sudo service nginx restart'
                }
            }
        }
    }
    post {
        always {
            // Send email notification
            mail to: 'laxmi.aadhavan1993@gmail.com',
                 cc: 'laxmi.aadhavan1993@gmail.com',
                 bcc: '',
                 subject: "${currentBuild.result}: ${env.JOB_NAME}",
                 body: """
                     Project: ${env.JOB_NAME}
                     Build Number: ${env.BUILD_NUMBER}
                     Build URL: ${env.BUILD_URL}
                     Result: ${currentBuild.result}
                 """
        }
    }
}
