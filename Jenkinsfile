pipeline {
    environment {
        mfiles = bat(script: 'git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d', returnStdout: true)
    }
    agent any
    stages {
        stage('Git Diff') {
            steps {
                script {
                    println(mfiles)
                    xcopy ${mfiles} """Target\""" /y
                }
            }
        }
    }
}
