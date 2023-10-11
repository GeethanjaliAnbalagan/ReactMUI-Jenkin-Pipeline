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
               

                // Install project dependencies
                sh 'npm install'

                // Build the React application
                sh 'npm run build'

              
            }
        }
    }
}
