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
        stage('package') {
            steps {
                bat 'mvn package'
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
        stage('Tomcat') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '8f9e4a48-90b7-4b3e-a2d3-6e6706eb89ae', path: '', url: 'http://localhost:8282/')], contextPath: 'pipeline_inti_github', war: '**/*.war'
            }
        }
    }
}
