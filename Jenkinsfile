pipeline {
    agent any
    stages {
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
    }
}
