pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                bat './gradlew test'
            }
            post {
                always {
                    junit '**/build/test-results/test/TEST-*.xml'
                }
            }
        }
        stage('Build') {
            steps {
                bat './gradlew clean build'
            }
        }
        stage('Sonar') {
            steps {
                withSonarQubeEnv(installationName: 'SonarQube') {
                  bat "./gradlew sonar"
                }
            }
        }
        /*stage('Deploy') {
            steps {
                build "jenkins-demo-deploy"
            }
        }*/
    }
}