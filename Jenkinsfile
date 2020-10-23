pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                sh 'maven3 clean package -DskipTests=true'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'maven3 surefire:test'
            }
        }
         stage('Integration Tests') {
            steps {
                sh 'maven3 failsafe:integration-test'
            }
        }
    }
    post {
        always {
            junit 'target/surefire-reports/TEST-*.xml'
        }
        failure {
            mail to: 'kiwaczki@gmail.com', subject: 'The Pipeline failed :(', body:'The Pipeline failed :('
        }
    }
}

