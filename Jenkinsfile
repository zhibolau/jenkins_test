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
    }
}
