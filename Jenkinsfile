pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat "mvn clean compile"
            }
        }
        stage('Test') {
            steps {
                bat "mvn test"
            }
        }
        stage('Deploy') {
            steps {
                bat "mvn package"                
            }
        } 
		stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('MySonarQube') {
                    bat "mvn sonar:sonar -Dsonar.token=sqa_0c758a06d0d31878ddb3c4c666f52c71f2415b2a"
                }				
            }
        }			
    }
}