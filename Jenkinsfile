pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
              deploy adapters: [tomcat9(credentialsId: 'Slim', path: '', url: 'http://54.159.194.45:8080/')], contextPath: 'Project', war: '"**/*.war"'
            }
        }
    }
}
