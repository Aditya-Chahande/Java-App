pipeline {
    environment {
        mfiles = bat'''git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=m, returnStdout: true'''
    }
    agent any
    stages {
        stage('Git Diff') {
            steps {
                script {
                    println(mfiles)
                }
            }
        }
    }
}
