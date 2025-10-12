pipeline
{
    agent  {
        label '1c_new'
    }

    environment {
        envString = 'true'
    }

    post {
        always {
            allure includeProperties: false, jdk: '', results: [[path: 'allure-results']]
            junit stdioRetention: 'ALL', testResults: 'out/syntax-check/junit/*.xml'
        }

        failure {
            bat "echo failure"
        }

        success {
            bat "echo success"
        }
    }

        
    stages {
        stage("Build test base") {
            steps {
                bat "chcp 65001\n vrunner init-dev"
                
            }            
        }    
        stage("Syntax check") {
            steps {
              bat "chcp 65001\n vrunner syntax-check"  
            }
        }

        stage("Run Functional Tests") {
            steps {
               bat "vrunner run --settings=env.json --profile=run-tests" 
            }
        }      
        
    }
}