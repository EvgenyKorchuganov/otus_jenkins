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
            bat "echo always"
        }

        failure {
            bta "echo failure"
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
        
    }
}