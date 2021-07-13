pipeline {
    agent any 
    stages {
        stage('Compile and clean') { 
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test -f /var/lib/jenkins/workspace/Maven_Sample_Pipeline/Maven_test_project/pom.xml" 
            }
        }
        stage('Deploy') { 
            steps {
                sh "mvn package -f /var/lib/jenkins/workspace/Maven_Sample_Pipeline/Maven_test_project/pom.xml" 
            }
        }
    }
}

