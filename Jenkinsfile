pipeline {
    agent any
    environment{
        REGISTRY = 'cirilimp'
        REPOSITORY = 'servidorweb'
        TAG = '1.0.7'
        DOCKER_HUB_LOGIN = credentials('cirilimp')
    }

    stages {
        stage('build') {
            steps {
                sh 'docker build -t $REPOSITORY:$TAG .'
                sh 'docker images'


            }
        }   
        stage('deploy') {
            steps {
                sh 'docker tag $REPOSITORY:$TAG $REGISTRY/$REPOSITORY:$TAG'
                sh 'docker login --username=$DOCKER_HUB_LOGIN_USR --password=$DOCKER_HUB_LOGIN_PSW'
                sh 'docker push $REGISTRY/$REPOSITORY:$TAG'
            }
        }         
    }
}
