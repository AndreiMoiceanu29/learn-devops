//CODE_CHANGES = getGitChanges()
def gv

pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
       // SERVER_CREDENTIALS = credentials('server-test-credentials')
    }
    // tools {
    //     maven
    // }
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: '')
        booleanParam(name: 'executeTest', defaultValue: true, description: '')
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }

        stage("build") {
            // when {
            //     expression{
            //          BRANCH_NAME == 'dev' && CODE_CHANGES == true
            //     }
            // }
            steps{
                script {
                    gv.buildApp()
                }
            }
        }

        stage("test") {
            when {
                expression{
                    params.executeTest
                }
            }
            steps{
                script {
                    gv.testApp()
                }
            }
        }

        stage("deploy") {
            steps{
                script {
                    gv.deployApp()
                }
                // withCredentials([
                //     usernamePassword(credentials: 'server-test-credentials',usernameVariable: USER, passwordVariable: PWD)
                // ]) {
                //     echo "runing some script with ${USER} and ${PWD}"
                // }
            }
        }
    }
    // post {
    //     always {
    //         // executed always even if the build fails
    //     }

    //     success {
    //         // only if the build succeded
    //     }

    //     failure {
    //         // only if the build failed
    //     }
    // }
}