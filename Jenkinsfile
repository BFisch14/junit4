pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            environment {
                Art_COMMON_CREDS = credentials('artifactory')
            }
            steps {
               sh 'curl -u $Art_COMMON_CREDS -X PUT "http://artifactory:8081/artifactory/libs-snapshot-local/com/devops-bootcamp/samples/junit619/junit/4.16-SNAPSHOT/junit-4.16-1.jar" -T ${WORKSPACE}/target/junit4.jar' 
            }
        }
    }
}