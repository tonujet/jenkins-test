pipeline {
    agent any

    triggers {
        pollSCM '*/1 * * * *'
    }

    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
    }

    parameters {
            string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

            text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

            booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

            choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

            password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {

        stage('init') {
            steps {
                script {
                    test = load "test.groovy"
                }
            }
        }

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
                script {
                     test.buildApp()
                }
                echo 'Hello deploy'
            }
        }

        stage('test') {
            steps {
                echo "Hello ${DISABLE_AUTH}"
                echo "Hello ${DB_ENGINE}"
            }
        }

        stage('Example') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }

    }
     post {
        always {
            echo 'I will always say Hello again!'
        }
     }
}
