pipeline {
    agent any
    tools {
        maven 'my-maven'
    }

    stages {
        stage('clone') {
            steps {
                git url: 'https://github.com/neda-vazharova/CICD-project1.git'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('code_review') {
            steps {
                sh 'mvn -P metrics pmd:pmd'
            }
        }
        stage('unit_test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('metric_check') {
            steps{
                sh 'mvn cobertura:cobertura -D cobertura.report.format=xml'
            }
        }
        stage('package') {
            steps{
                sh 'mvn package'
            }
        }
    }
}
