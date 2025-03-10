pipeline {   
    agent any 
    
    tools {
        jdk 'jdk17'
        maven 'mvn3.9'
    }

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SruthikRoshanBatchu/springboot-java-poject.git'
            }
        }
        
        stage('Compile') {
            steps {
                sh "mvn compile"
            }
        }
        
        stage('Package') {
            steps {
                sh "mvn clean package"
            }
        }

        stage('Test') {
            steps {
                sh "mvn test"
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sample') {  
                    sh "mvn clean verify sonar:sonar -Dsonar.projectKey=sample -Dsonar.projectName='sample' -Dsonar.host.url=http://your-sonarqube-server:9000"
                }
            }
        }
    }
}
