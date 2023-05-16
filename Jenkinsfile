pipeline {
    agent any
    stages{
        stage ('continuous Download'){
            steps{
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continous Build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('continuous Deployment'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '96d4b5e1-d178-45a7-9286-7c41cd24b30d', path: '', url: 'http://172.31.29.141:8080')], contextPath: 'venupath', war: '**/*.war'
            }
        }
        stage('continuous Teting'){
            steps{
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/tomcat9/testing.jar'
            }
        }
    }
}