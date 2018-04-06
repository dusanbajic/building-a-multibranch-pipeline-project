pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000 -p 5000:5000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh '''mkdir ~/.npm-global
                    npm config set prefix '~/.npm-global'
                    export PATH=~/.npm-global/bin:$PATH
                    source ~/.profile
                    npm install'''
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}