pipeline {
    agent any

    stages {
        stage('Download and Deploy index.html') {
            steps {
                script {
                    // Define the URL of the index.html file
                    def url = 'https://raw.githubusercontent.com/HASNAIN005/tocs/main/index.html'

                    // Download the index.html file using curl and store its content
                    def htmlContent = sh(script: "curl -s ${url}", returnStdout: true).trim()

                    // Print the content of the index.html file
                    echo "Content of index.html:"
                    echo htmlContent

                    // Write the content to a temporary file
                    def tempFile = writeFile file: 'index.html', text: htmlContent

                    // Copy the index.html file to the server using SCP
                    sh "scp ${tempFile} user@server_ip:/var/www/html/index.html"
                }
            }
        }
    }
}
