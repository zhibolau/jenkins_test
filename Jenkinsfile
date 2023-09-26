pipeline {
    agent any
    stages {
        stage('docker-agent-Test') {
            agent {
                docker { image 'node:latest' }
            }
            steps {
                sh 'node --version'
            }
        }
        stage('build') {
            steps {
                sh 'java --version'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
        stage('Deploy') {
            steps {
                retry(3) {
                    sh 'echo "DeployING---->"'
                }

                timeout(time: 3, unit: 'MINUTES') {
                    sh 'echo "health-check ING--->"'
                }
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Succeed------->!"; exit 0'
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
