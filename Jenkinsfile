pipeline {
    agent any
    stages {
        stage ('nginx installation') {
              steps {
            sh 'sudo yum install nginx -y'
            sh 'sudo service nginx start'
            }
       }
        stage ('copying the path') {
              steps {
                sh 'sudo cp -r /root/workspace/pipe17/* /usr/share/nginx/html/'
                sh 'sudo service nginx restart'
            }
        }
        }
   }
