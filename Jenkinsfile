pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Ensure you have Git installed on your Windows Jenkins agent
                bat 'git clean -xdf'  // Optional: Clean up any untracked files
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Set up Node.js (configured in Jenkins Global Tool Configuration)
                    def nodeHome = tool name: 'NodeJS', type: 'Tool'
                    def npmHome = tool name: 'npm', type: 'Tool'
                    
                    // Change to the project directory where your package.json is located
                    dir('path/to/your/project') {
                        bat "cd path/to/your/project && ${nodeHome}\\npm install"
                        bat "cd path/to/your/project && ${nodeHome}\\npm run build"
                    }
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts(allowEmptyArchive: true, artifacts: '*/build/*')
        }
    }
}
