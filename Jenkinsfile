pipeline {
    agent any
    stages {
        stage('Detect Changes') {
            steps {
                script {
                    def mfiles = bat(script: 'git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d', returnStdout: true).trim()
                    echo mfiles
                    if(mfiles) {
                        mfiles.split('\n').each { file ->
                            echo file
                            bat "xcopy /f /e /i /y \"${file}\"C:\ProgramData\Jenkins\.jenkins\workspace\Java App\target"
                        }
                    } else {
                        echo "No modified files"
                    }
                    def dfiles = bat(script: 'git diff --diff-filter=D --name-only --summary %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% | findstr /r "delete"', returnStdout: true).trim()
                    if(dfiles) {
                        echo dfiles >> "Target\\dfiles.txt"
                    } else {
                        echo "No deleted files"
                    }
                    if(!mfiles && !dfiles) {
                        echo "NO changes found"
                        error("No changes found")
                    } else {
                        echo "Changes delivered to target folder"
                    }
                }
            }
        }
    }
}
