pipeline {
    agent any

    environment {
        SSH_CREDENTIALS_ID = '123' // Update with the actual ID of your credentials
        REMOTE_USER = 'HASNIAN' // Update with your actual username
        REMOTE_HOST = '35.202.20.149' // Update with your remote server's IP address or hostname
        REMOTE_DOC_ROOT = '/var/www/html' // Update with the path to your document root
    }

    stages {
        stage('Download index.html') {
            steps {
                script {
                    def url = 'https://raw.githubusercontent.com/HASNAIN005/tocs/main/index.html'
                    sh "curl -s ${url} -o index.html"
                }
            }
        }
        stage('Deploy index.html to Apache') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: env.SSH_CREDENTIALS_ID, usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh """
                            sshpass -p ${PASSWORD} scp index.html ${USERNAME}@${env.REMOTE_HOST}:${env.REMOTE_DOC_ROOT}/index.html
                        """
                    }
                }
            }
        }
    }
}
