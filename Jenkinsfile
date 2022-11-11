pipeline {
    agent any
    tools { 
        maven 'Maven 3.8.6' 
        jdk 'OpenJDK 19' 
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/markot99/jenkins_spring_example.git']]])
            }
        }
        stage('Validate files') {
            steps {
                sh "mvn validate"
            }
        }
        stage('Compile files') {
            steps {
                sh "mvn compile"
            }
        }
        stage('Test files') {
            steps {
                sh "mvn test"
            }
        }
        stage('Package files') {
            steps {
                sh "mvn package"
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        stage('Clean workspace') {
            steps {
                cleanWs()
            }
        }
    }
}
