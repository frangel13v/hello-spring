pipeline {
    agent any
    
    options {
        timestamps()
        ansiColor('xterm')
    }

    stages {
        stage('Start') {
            steps {
                sh './mvnw compile'
                sh './mvnw test'
                sh './mvnw package'
                sh 'java -jar target/testing-web-complete-0.0.1-SNAPSHOT.jar'
            }
        }
        stage('Build') {
            steps {
                sh 'docker-compose build'
            }
        }
        stage('Deploy') {
            steps {
                sh '''docker-compose up -d
                docker-compose logs -t --tail=10 
                '''
            }
        }
    
    }
}
