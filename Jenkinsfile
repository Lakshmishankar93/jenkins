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
                sh 'sudo cp -r /var/lib/jenkins/workspace/pipeabi/index.html /usr/share/nginx/html/'
                sh 'sudo service nginx restart'
            }
        }
        post {
            always {
               mail bcc: 'laxmi.aadhavan1993@gmail.com', body: """project=>${env.JOB_name}
   build number=>${env.BUILD_NUMBER}
   url=>${env.BUILD_URL}
Result:=>${currentBuild.result}""", cc: 'laxmi.aadhavan1993@gmail.com', from: '', replyTo: '', subject: "${currentBuild.result}", to: 'laxmi.aadhavan1993@gmail.com'                 
        }
   }
}
}

