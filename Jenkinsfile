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
                        properties: [],
                        reportBuildPolicy: 'ALWAYS',
                        results: [[path: 'test-results']],
                        report: 'test-results'
                      ])
                    }
                }
            }
        }
        
        stage('Publish') {
        echo 'Publish Allure report'
        publishHTML(
                target: [
                        allowMissing         : false,
                        alwaysLinkToLastBuild: false,
                        keepAll              : true,
                        reportDir            : 'test-results',
                        reportFiles          : 'index.html',
                        reportName           : "Allure Report"
                ]
            )
         }
       
    }
}
