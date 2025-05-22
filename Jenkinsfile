pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = "my-spring-boot-app"
        DOCKER_IMAGE_TAG = "latest" 
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout SCM
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh './mvnw clean package -DskipTests'
                    } else {
                        bat '.\\mvnw.cmd clean package -DskipTests'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        sh './mvnw test'
                    } else {
                        bat '.\\mvnw.cmd test'
                    }
                }
                // Example: JUnit test results publisher
                // junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Code Quality') {
            steps {
                echo "Executing Code Quality checks (e.g., SonarQube integration)..."
                // In a real scenario, you would integrate with SonarQube or another tool here.
                // sh "./mvnw sonar:sonar"
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}..."
                sh "docker build -t ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG} ."
            }
        }

        stage('Publish Docker Image') {
            steps {
                // In a real scenario, you would push to a Docker registry (e.g., Docker Hub, ECR, GCR)
                // withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'DOCKER_HUB_PASSWORD', usernameVariable: 'DOCKER_HUB_USERNAME')]) {
                //     sh "docker login -u ${DOCKER_HUB_USERNAME} -p ${DOCKER_HUB_PASSWORD}"
                //     sh "docker push ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                // }
                echo "Simulating Docker image publish for ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}."
                sh "docker images ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
            // Clean up workspace, etc.
            // cleanWs() 
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
