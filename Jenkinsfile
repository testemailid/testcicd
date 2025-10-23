pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'Maven3'
    }

    stages {
        stage('Checkout') {
            steps {
            echo 'checking out source code from Github...'
                git branch: 'main',
                    url: 'https://github.com/testemailid/testcicd.git'
                    }
            }
        stage('Build') {
            steps{
                echo 'Running Maven clean and compile...'
                sh 'mvn clean compile'
            }
        }
        stage('Run Application') {
            // write your logic here
            steps{
                echo 'run the test case'
                sh 'mvn test'
            }
        }
        stage('Test') {
            // write your logic here
            steps{
                echo 'report'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
