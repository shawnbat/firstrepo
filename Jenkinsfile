pipeline {
    //agent any
	agent {
        docker { image 'node:7-alpine' }
    }
    stages {
        stage('Build') {
            steps {
				echo "[*] Starting build (id: ${env.BUILD_ID}) on ${env.JENKINS_URL}"
                sh 'echo "We Building"'
                sh '''
                    echo "Multiline shell steps works too in Build stage"
                    ls -lah
                '''
				echo "Hello World!"
                sh "echo Hello from the shell"
                sh "hostname"
                sh "uptime"
            }
        }
		stage('Test') {
            steps {
                sh 'echo "We Testing"'
                sh '''
                    echo "Multiline shell steps works too in Test stage"
                    ls -lah
					node --version
                '''
            }
        }
		stage('Deploy') {
            steps {
                sh 'echo "We Deploying now"'
                sh '''
                    echo "Multiline shell steps works too in Deploy stage"
                    ls -lah
					echo "Working directory is:  "
					pwd
                '''
				/* retry(2) {
                    sh './flakey-deploy.sh'
                }
				*/
                timeout(time: 1, unit: 'MINUTES') {
				sh 'id'
                    // sh 'whoami'
				
				sh 'sudo sh ./health-check.sh'
                }
				
            }
        }
    }
	
	post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
