pipeline {
    agent any
    stages {
        stage ('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/saddam2727/maven.war.git'
            }
        }
        stage ('validate the project') {
            steps {
                sh 'mvn validate'
            }
        }
        stage ('compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage ('test the project') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('package the project') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('deployement') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://192.168.29.168:8087/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
