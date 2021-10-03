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
                            includeProperties: true,
                            jdk: '',
                            displayName: 'Marina New Report',
                            properties: [],
                            reportBuildPolicy: 'ALWAYS',
                            results: [[path: 'test-results']],
                            report: 'test-results'
                          ])
                    }
                }
            }
        }
      
    }
}
