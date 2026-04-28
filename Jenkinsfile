pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sivareddy78936/sign-in-.git'
            }
        }

        stage('Backend Install') {
            steps {
                dir('Backend') {
                    sh 'npm install'
                }
            }
        }

        stage('Backend Test') {
            steps {
                dir('Backend') {
                    sh 'npm test || echo "No tests"'
                }
            }
        }

        stage('Frontend Install') {
            steps {
                dir('Frontend') {
                    sh 'npm install'
                }
            }
        }

        stage('Frontend Build') {
            steps {
                dir('Frontend') {
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'ansible-playbook -i inventory deploy.yml'
            }
        }
    }
}
