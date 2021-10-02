pipeline {
    agent any
    stages {
        stage('build') {
            steps {
              //  sh 'python --version'
                sh 'pytest /Users/marina.kur/Documents/CustomProjects/pytests/test_sample.py'
            }
            post {
              always {
                    script {
                      allure([
                        includeProperties: false,
                        jdk: '',
                        properties: [],
                        reportBuildPolicy: 'ALWAYS',
                        results: [[path: 'target/allure-results']]
                      ])
                    }
                }
            }
        }
    }
}
