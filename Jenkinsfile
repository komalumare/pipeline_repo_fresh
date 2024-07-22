pipeline {
    agent any

    stages {
        stage('clean') {
            steps {
                bat 'mvn clean'
            }
        }
      stage('test') {
            steps {
                bat 'mvn test'
            }
        }
      stage('install') {
            steps {
                bat 'mvn install'
            }
        }
        stage('Results') {
            steps {
                input 'do you want to proceed'
                junit '**/target/surefire-reports/TEST-*.xml'
                archiveArtifacts 'target/*.jar'
            }
        }
        stage('Email') {
            steps {
                mail bcc: '', body: 'this is a mial from the declarative pipeline', cc: '', from: '', replyTo: '', subject: 'regarding declarative pipeline', to: 'te415606@gmail.com'
            }
        }
    }
}
