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
                sh 'ls'
            }
        }
        stage('Docker'){
            steps{
            sh 'docker build -t dockerdb ./Docker-db'
            sh 'docker build -t webapp -f Docker-app/Dockerfile .'
            }
        }
        stage('Deploy'){
            steps{
                sh 'docker run -d --name devopsdb -p 3306:3306 dockerdb'
                sh 'docker run -d --name appcont -p 8082:8080 --link devopsdb:mysqlcon webapp'

            }
        }
        
    }
}
