pipeline {
    agent any

    stages {
        stage('Download and Display index.html') {
            steps {
                script {
                    // Define the URL of the index.html file
                    def url = 'https://raw.githubusercontent.com/HASNAIN005/tocs/main/index.html'

                    // Download the index.html file using curl and store its content
                    def htmlContent = sh(script: "curl -s ${url}", returnStdout: true).trim()

                    // Print the content of the index.html file
                    echo "Content of index.html:"
                    echo htmlContent

                    // Save the content to a file
                    writeFile file: 'index.html', text: htmlContent

                    // Copy the index.html file to the server using SCP
                    // Replace 'user' with your actual username and '35.202.20.149' with your server IP
                    sh "scp -i ~/.ssh/id_rsa index.html ar784419@35.202.20.149:/var/www/html/"
                }
            }
        }
    }
}
