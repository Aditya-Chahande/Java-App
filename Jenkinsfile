pipeline {
    agent any
    stages {
        stage('Detect Changes') {
            steps {
                script {
                    def mfiles = bat(script: 'git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d', returnStdout: true).trim()
                    echo mfiles
                    echo mfiles
                    echo mfiles
                    script {
                    if ( ! -z "$mfiles" );
                    then
                        echo "$mfiles" | while IFS= read -r line ; do echo $line; cp -rf --parents "$line" Target; done
                    else
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
