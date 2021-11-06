
def gv

pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('server-credentials')
    }
    stages {
        stage {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build") {
            steps {
                echo 'building the application...'
                echo "building version ${NEW_VERSION}"
                script {
                    gv.buildApp()
                }
            }
        }

        stage("test") {
            when {
                expression {
                    BRANCH_NAME == 'main' || BRANCH_NAME =='master' 
                }
            }
            steps {
                echo 'testing the application...'
                script {
                    gv.testApp()
                }
            }
        }

        stage("deploy") {
            steps {
                echo 'deploying the application...'
               
            }
        }
    }
}