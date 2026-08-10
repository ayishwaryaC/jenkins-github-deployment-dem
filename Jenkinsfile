pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh 'test -f index.html'
                sh 'grep -q "hello from ayishu" index.html'
            }
        }

        stage('Build') {
            steps {
                sh 'mkdir -p build'
                sh 'cp index.html build/index.html'
            }
        }

        stage('Package') {
            steps {
                sh 'tar -czf website.tar.gz -C build .'
            }
        }

        stage('Deploy') {
            steps {
                archiveArtifacts artifacts: 'website.tar.gz',
                                 fingerprint: true
            }
        }
    }
}
