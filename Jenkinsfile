pipeline {
    agent any
    tools{
        maven 'maven'
    }
    stages {
        stage('SCM') {
            steps {
                git 'https://github.com/manju9676/dockerwebapp.git'
                sh 'ls'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('Docker'){
            steps{
            sh 'docker build -t dockerdb ./Docker-db'
            sh 'docker run -d --name dockerdb -p 3306:3306 dockerdb'
            sh 'docker build -t webapp ./Docker-app'
            sh 'docker run -d --name app -p 8082:8080 --link dockerdb webapp'
            }
        }
        
    }
}
