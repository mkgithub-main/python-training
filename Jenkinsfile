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
                            properties: [[key: 'allure.display.name', value: 'New Report']],
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
