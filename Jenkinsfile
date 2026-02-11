pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-lab:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 devops-lab:v1'
            }
        }
    }
}
