pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000 -p 5000:5000'
        }
    }

    environment {
        CI = 'true'
        NPM_CONFIG_PREFIX = '/tmp/.npm-global'
    }

    stages {
        stage('Build') {
            steps {
                sh 'env'
                sh 'pwd'
                sh 'touch foo'
                sh 'ls -la'
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}