pipeline {
    agent any
    
    environment {
        NODEJS_HOME = tool name: 'NodeJS', type: 'Tool'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    def npm = tool name: 'npm', type: 'Tool'
                    sh "${npm} install"
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    def npm = tool name: 'npm', type: 'Tool'
                    sh "${npm} run build"
                }
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                script {
                    // Replace this with your deployment script
                    sh 'echo "Deployment script goes here"'
                }
            }
        }
    }

    post {
        always {
            // Archive your build artifacts (e.g., build directory) for later reference.
            archiveArtifacts 'build/**'
        }
    }
}
