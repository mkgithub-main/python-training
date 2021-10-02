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
                  
                    script {
                        def htmlFiles
                        dir ('reports') {
                            htmlFiles = findFiles glob: '*.html'
                        }
                        publishHTML(
                                target: [
                                        allowMissing         : true,
                                        alwaysLinkToLastBuild: true,
                                        keepAll              : true,
                                        reportDir            : 'test-results',
                                        reportFiles: htmlFiles.join(','),
                                        reportName           : 'Allure Report',
                                        reportTitles         : 'The Report'
                                ]
                        )
                    }
                }
            }
        }
      
    }
}
