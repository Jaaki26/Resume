pipeline {
  agent any
  environment {
    AWS_DEFAULT_REGION = 'us-east-1'
    ECR_REGISTRY = "${env.AWS_ACCOUNT_ID}.dkr.ecr.${env.AWS_DEFAULT_REGION}.amazonaws.com"
    ECR_REPO = "resume-site"
    IMAGE_TAG = "${env.BUILD_NUMBER}"
  }
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Build') { steps { sh 'mvn -B -DskipTests package || true' } }
    stage('Build Docker Image') { steps { sh 'docker build -t ${ECR_REPO}:${IMAGE_TAG} .' } }
  }
}
