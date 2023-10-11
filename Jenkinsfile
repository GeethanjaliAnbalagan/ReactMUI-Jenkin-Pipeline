pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Set up Node.js (you should configure Node.js in Jenkins Global Tool Configuration)
                    def nodeHome = tool name: 'NodeJS', type: 'Tool'
                    def npmHome = tool name: 'npm', type: 'Tool'

                    sh "${nodeHome}/bin/npm install"
                    sh "${nodeHome}/bin/npm run build"
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
