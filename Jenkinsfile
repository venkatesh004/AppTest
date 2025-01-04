pipeline {
    agent none

    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                script {
                    // Move to the backend folder
                    dir('backend') {
                        // Run Maven build
                        sh 'mvn clean install'
                    }
                }
            }
        }

        stage('Front-end') {
            agent {
                docker { image 'node:16-alpine' }
            }
            steps {
                script {
                    // Move to the frontend folder
                    dir('frontend') {
                        // Install Node.js dependencies
                        sh 'npm install'
                        // Run build or other npm commands
                        sh 'npm run build' // Or any other command based on your package.json
                    }
                }
            }
        }
    }
}

