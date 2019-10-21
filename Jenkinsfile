pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "We Bulding"'
                sh '''
                    echo "Multiline shell steps works too in Build stage"
                    ls -lah
                '''
            }
        }
		stage('Test') {
            steps {
                sh 'echo "We Testing"'
                sh '''
                    echo "Multiline shell steps works too in Test stage"
                    ls -lah
                '''
            }
        }
		stage('Deploy') {
            steps {
                sh 'echo "We Deploying now"'
                sh '''
                    echo "Multiline shell steps works too in Deploy stage"
                    ls -lah
                '''
            }
        }
    }
}