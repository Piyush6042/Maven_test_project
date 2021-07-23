pipeline {
    agent any 
    stages {
        stage('Compile and clean') { 
            steps {
                sh "mvn clean compile"
                sh "printenv"
            }
                post { 
        always { 
           junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
        }
    }
        }
        stage('Docker build image') { 
            steps {
                sh "docker build -t piyush6042/jenkins:$(BUILD_NUMBER) ." 
            }
        }
        stage('Docker hub login') { 
            steps {
                withCredentials([string(credentialsId: 'dockerhub11', variable: 'dockerpwd')])
                sh "docker login -u piyush6042 -p ${dockerpwd}" 
            }
        }
        stage('Push image to Docker hub') { 
            steps {
                sh "docker push piyush6042/jenkins:$(BUILD_NUMBER)" 
            }
        }
          stage('Deploy') { 
            steps {
                sh "mvn package -f /var/lib/jenkins/workspace/Maven_Sample_Pipeline/Maven_test_project/pom.xml" 
            }
        }

        stage('Deploy') { 
            steps {
                sh "mvn package -f /var/lib/jenkins/workspace/Maven_Sample_Pipeline/Maven_test_project/pom.xml" 
            }
        }
    }
}
