pipeline {
    agent any

    environment {
        NODE_HOME = "/usr/local/bin" // Adjust this path if Node.js is installed in a different directory
        PATH = "$NODE_HOME:$PATH"
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                git 'https://github.com/yourusername/your-nodejs-repo.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install dependencies defined in package.json
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                // Run tests defined in package.json
                sh 'npm test'
            }
        }

        stage('Build') {
            steps {
                // Run build script defined in package.json (if applicable)
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application
                // Example: Copy files to a specific directory or restart a service
                sh '''
                cp -R * /path/to/deploy/
                pm2 restart all
                '''
            }
        }
    }

    post {
        always {
            // Clean up workspace
            cleanWs()
        }
    }
}

