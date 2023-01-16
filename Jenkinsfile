mfiles=$(git diff %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% --name-only --diff-filter=d)
        - echo $mfiles
        - |
            if [ ! -z "$mfiles" ];
            then
            echo "$mfiles" | while IFS= read -r line ; do echo $line; cp -rf --parents "$line" Target; done
               #cp -rv --parents "$mfiles" Target;
            else
                echo "No modified files";
            fi
        # Deleted Files
        - dfiles=$(git diff --diff-filter=D --name-only --summary %GIT_PREVIOUS_COMMIT% %GIT_COMMIT% | grep delete || true) 
        - if [ ! -z "$dfiles" ];
            then
                echo $dfiles >> Target/dfiles.txt;
            else
                echo "No deleted files";
            fi
        # If there are no modified files or deleted files
        - if [[ -z $dfiles && -z $mfiles ]];
            then
                echo "NO changes found";
                exit 1;
            else
                echo "Changes delivered to target folder";
            fi
