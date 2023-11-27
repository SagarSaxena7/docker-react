pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'devimage'
    }
    
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Assuming Dockerfile.dev is in the root directory
                    sh 'docker build -t $DOCKER_IMAGE -f Dockerfile.dev .'
                }
            }
        }
        
        stage('Run Tests') {
            steps {
                script {
                    // Assuming your npm run test command includes the necessary options
                    sh 'docker run -e CI=true $DOCKER_IMAGE npm run test -- --coverage'
                }
            }
        }
    }
}
