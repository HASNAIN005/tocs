pipeline {
    agent any

    environment {
        // Define the SSH credentials ID in Jenkins
        SSH_CREDENTIALS_ID = '123' // Update this with the actual ID of your credentials
        // Define the remote server details
        REMOTE_USER = 'ar784419' // Update this with your actual username
        REMOTE_HOST = '35.202.20.149' // Update this with your remote server's hostname or IP address
        // Define the path to the document root on the remote server
        REMOTE_DOC_ROOT = '/var/www/html'
    }

    stages {
        stage('Download index.html') {
            steps {
                script {
                    // Define the URL of the index.html file
                    def url = 'https://raw.githubusercontent.com/HASNAIN005/tocs/main/index.html'

                    // Download the index.html file using curl and store it in a workspace file
                    sh "curl -s ${url} -o index.html"
                }
            }
        }
        stage('Deploy index.html to Apache') {
            steps {
                script {
                    // Copy the index.html file to the remote server's document root using SSH key authentication
                    sshagent(credentials: [SSH_CREDENTIALS_ID]) {
                        sh "scp index.html ${REMOTE_USER}@${REMOTE_HOST}:${REMOTE_DOC_ROOT}/index.html"
                    }
                }
            }
        }
    }
}
