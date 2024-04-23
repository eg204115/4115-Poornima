pipeline {
    agent any 
   
    
    stages { 
        stage('SCM Checkout') {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/HGSChandeepa/test-node'
                }
            }
        }
        stage('Build Docker Image') {pipeline {
    agent any 
    
    stages { 
        stage('SCM Checkout') {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/eg204115/4115-Poornima.git'
                }
            }
        }
        stage('Build Docker Image') {
            steps {  
                sh "docker build -t eg204115/test-app-image:${BUILD_NUMBER} ."
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'ass2-devops', variable: 'var-ass2')])  {
                    sh "docker login -u eg204115 -p ${var-ass2}"
                }
            }
        }
        stage('Push Image') {
            steps {
                sh "docker push eg204115/test-app-image:${BUILD_NUMBER}"
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}

            steps {  
                bat 'docker build -t adomicarts/nodeapp-cuban:%BUILD_NUMBER% .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                withCredentials([string(credentialsId: 'samin-docker', variable: 'samindocker')]) {
   
               bat'docker login -u adomicarts -p ${samindocker}'
                }
            }
        }
        stage('Push Image') {
            steps {
                bat 'docker push adomicarts/nodeapp-cuban:%BUILD_NUMBER%'
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}