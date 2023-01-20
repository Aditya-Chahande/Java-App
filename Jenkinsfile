pipeline {
    agent any
    stages {
        stage('Git Diff') {
            steps {
                script {
                    def mfiles = bat(script: 'git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d', returnStdout: true).trim()
                    println(mfiles)
                    for /f "delims=" %i in ('echo ${mfiles}') do (
                            echo %i
                            xcopy /S /I /Y "%i" Target
                        )
                }
            }
        }
    }
}
