pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-lab-app"
        IMAGE_TAG = "v1"
    }

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/jaabhilash13/devops-lab-app.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Stop previous container if running
                    sh "docker rm -f ${IMAGE_NAME} || true"
                    // Run new container
                    sh "docker run -d --name ${IMAGE_NAME} -p 5000:5000 ${IMAGE_NAME}:${IMAGE_TAG}"
                }
            }
        }

    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}

