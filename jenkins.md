pipeline {
    agent any

    stages {

        stage('Cloning the code') {
            steps {
                git url: 'https://github.com/himani0550/FlaskTest_exam/tree/main', branch: 'main'
            }
        }
        stage('Install requirements') {
            steps {
                script {
                    dir('FlaskTest') {
                        sh 'pip3 install -r requirements.txt'
                    }
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    dir('FlaskTest') {
                        sh 'python3 test_app.py'
                    }
                }
            }
        }
    }
}
