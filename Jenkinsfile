pipeline {
    environment {
        mfiles = bat'''git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d'''
    }
    agent any
    stages {
        stage('Git Diff') {
            steps {
                echo "${mfiles}"
            }
        }
    }
}
