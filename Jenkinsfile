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
        stage('Setup Git') {
            steps {
                sh '''
                    git config --global http.postBuffer 1048576000   # 1 ГБ
                    git config --global https.postBuffer 1048576000
                    git config --global http.lowSpeedLimit 0
                    git config --global http.lowSpeedTime 999999
                '''
            }
        }
        stage('Checkout') {
            steps {
                retry(3) {
                    checkout scm
                }
            }
        }
    }
    
    stages {
        stage("Build test base") {
            steps {
                bat "chcp 65001\n vrunner init-dev --v8version 8.3.26.1581 --dt C:\\jenkins_agent\\1c_new\\template\\1Cv8.dt --db-user Администратор --src C:\\Lesson30\\Repo_Git\\src --ibconnection /Slocalhost\bsp" 
                //bat "echo Buil test base"
            }
        }       
        
    }
}