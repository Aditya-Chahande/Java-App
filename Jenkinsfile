pipeline {
    agent any
    stages {
        stage('Git Diff') {
            steps {
                script {
                    def mfiles = bat(script: 'git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d', returnStdout: true).trim()
                    println(mfiles)
                    echo mfiles | while IFS= read -r line
                    do echo line
                    cp -rf --parents line Target;
                }
            }
        }
    }
}
