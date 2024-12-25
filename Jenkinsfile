pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('1')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh ' docker build -t saikrupakatta/saikrupakatta_2019:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh ' docker push saikrupakatta/saikrupakatta_2019:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }

    }
}
