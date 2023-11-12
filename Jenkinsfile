pipeline {
    agent any
    
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    stages {
        stage('build') {
            when {
                expression {
                    BRANCH_NAME != "main"
                }
            }
            steps {
                echo "Branch: ${BRANCH_NAME}"
            }
        }

        stage('delpoy') {
            steps {
                echo 'Hello deploy'
            }
        }

        stage('test') {
            steps {
                echo "Hello ${DISABLE_AUTH}"
                echo "Hello ${DB_ENGINE}"
            }
        }

    }
     post {
        always {
            echo 'I will always say Hello again!'
        }
     }
}
