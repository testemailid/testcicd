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
                sh 'mvn clean install -DskipTests'
            }
        }
        stage('Run unit test') {
            steps{
                echo 'run the test case'
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }         
        }
 }
        post {
             success {
                 echo 'Build succeeded!'
             }
            failure {
               echo 'Build failed. check console' 
            }
        }
    }

