pipeline {
     agent {
        label 'master'
    }
    
    environment {
        DOCKER_IMAGE = 'devimage'
        DOCKERFILE_PATH = '/var/lib/jenkins/workspace/PipelinetoGitHUB/Dockerfile.dev'
    }
    
    stages {
        stage('Example Stage') {
            steps {
                echo 'Hello, this job is running on the Jenkins master node!'
                // Add your build steps here
            }
            
        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t $DOCKER_IMAGE -f $DOCKERFILE_PATH ."
                }
            }
        }
        
        stage('Run Tests') {
            steps {
                script {
                    sh "docker run -e CI=true $DOCKER_IMAGE npm run test -- --coverage"
                }
            }
        }
    }
}