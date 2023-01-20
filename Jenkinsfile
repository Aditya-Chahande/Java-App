pipeline {
    agent any
    stages {
        stage('Detect Changes') {
            steps {
                    def mfiles = bat(script: 'git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d', returnStdout: true).trim()
                    echo mfiles
                   
                }
            }
        }
    }
