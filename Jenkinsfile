pipeline {
    agent any
    stages {
        stage('build') {
            steps {
              //  sh 'python --version'
                sh 'pytest /Users/marina.kur/Documents/CustomProjects/pytests/test_sample.py'
                
                allure([
                        includeProperties: true,
                        jdk              : '',
                        properties       : [],
                        reportBuildPolicy: 'ALWAYS',
                        results          : 'test_reports_results',
                        report           : 'test_reports_report',
                        allurePrefix     : 'test_reports_prefix'
                ])
            }
        }
    }
}
