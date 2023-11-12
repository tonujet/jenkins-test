pipeline {
    agent any
    
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }
    
    stages {
        stage('build') {
            when {
                expression{
                    env.BRANCH_NAME != main
                }
            }
            steps {
                echo 'Hello build'
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
}
