pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')  // Add in Jenkins UI
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/yatindrap6/devops-microservices-project.git'
            }
        }

        stage('Build & Push User Service') {
            steps {
                dir('user-service') {
                    script {
                        sh 'docker build -t yatindrap6/user-service .'
                        sh 'echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u "$DOCKERHUB_CREDENTIALS_USR" --password-stdin'
                        sh 'docker push yatindrap6/user-service'
                    }
                }
            }
        }

        stage('Build & Push Product Service') {
            steps {
                dir('product-service') {
                    script {
                        sh 'docker build -t yatindrap6/product-service .'
                        sh 'docker push yatindrap6/product-service'
                    }
                }
            }
        }

        stage('Build & Push Frontend') {
            steps {
                dir('frontend') {
                    script {
                        sh 'docker build -t yatindrap6/frontend .'
                        sh 'docker push yatindrap6/frontend'
                    }
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}

