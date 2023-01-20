pipeline {
    agent any
    stages {
        stage('Git Diff') {
            steps {
                script {
                    def mfiles = bat(script: 'git diff ${env.GIT_PREVIOUS_COMMIT} ${env.GIT_COMMIT} --name-only --diff-filter=d', returnStdout: true).trim()
                    println(mfiles)
                }
            }
        }
    }
}
