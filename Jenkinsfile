pipeline {
    agent any
    stages {
        stage('Git Diff') {
            steps {
                mfiles = bat'''git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d'''
                bat "echo ${mfiles}"
            }
        }
    }
}
