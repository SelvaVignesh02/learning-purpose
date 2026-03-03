pipeline {
    agent any
    tools {
        maven 'M2'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                deploy adapters: [
                    tomcat9(
                        credentialsId: 'tomcat',
                        path: '',
                        url: 'http://13.201.12.148:8080'
                    )
                ],
                contextPath: 'mywebapp',
                onFailure: false,
                war: '**/*.war'
            }
        }
    }
}
