//CODE_CHANGES = getGitChanges()
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
        stage("build") {
            // when {
            //     expression{
            //          BRANCH_NAME == 'dev' && CODE_CHANGES == true
            //     }
            // }
            steps{
                echo 'building the application...'
                echo "building version ${NEW_VERSION}"
            }
        }

        stage("test") {
            when {
                expression{
                    params.executeTest
                }
            }
            steps{
                echo 'testing the application...'
            }
        }

        stage("deploy") {
            steps{
                echo 'deploying the application'
                echo "deploying version ${params.VERSION}"
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