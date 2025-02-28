pipeline {
    agent any
    
    environment {
        SONAR_URL = 'http://34.27.111.131:9000'
        SONAR_TOKEN = credentials('sonar-token')  // Add this in Jenkins credentials
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Saicharan619/mvnsonardoc.git'
            }
        }
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                sh '''
                mvn sonar:sonar \
                    -Dsonar.projectKey=my-project \
                    -Dsonar.host.url=${SONAR_URL} \
                    -Dsonar.token=${SONAR_TOKEN}
                '''
            }
        }
    }
}
