pipeline {
    agent {
        docker {
            image 'mhart/alpine-node:6'
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
                sh '#export HOME=$(pwd)'
                sh 'env'
                sh '# mkdir /tmp/.npm-global'
                sh '#npm config set prefix "/tmp/.npm-global"'
                sh '#export PATH=/tmp/.npm-global/bin:$PATH'
                sh '#env'
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