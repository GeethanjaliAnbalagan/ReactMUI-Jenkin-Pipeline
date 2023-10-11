pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from the repository
                checkout scm
            }
        }

        stage('Build and Deploy') {
            steps {
                // Install Node.js and NPM
                sh 'curl -sL https://deb.nodesource.com/setup_14.x | bash -'
                sh 'apt-get install -y nodejs'

                // Install project dependencies
                sh 'npm install'

                // Build the React application
                sh 'npm start'

                // Deploy to a web server (customize this step)
                // For a simple example, you can copy the build folder to a web server
                sh 'rsync -av build/ /var/www/html/'
            }
        }
    }
}
