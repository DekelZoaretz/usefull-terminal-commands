# Usefull Terminal commands

## Bash

 - running processes ```$ ps aux```
 - kill running processes by pattern ```$ pkill -f <PATTERN>  ```
 - get my public IP ```$ hostname -I | awk '{print $1}'```
 - view system information using neofetch ```$ neofetch``` 
 - get folder size - ```$ du -hs <FOLDER_NAME>```
 - get disc size - ```$ df -H``` - The size is displayed in the unit of "H" which stands for "Human-readable" and uses powers of 1000 (i.e., 1 kilobyte = 1000 bytes).
 - Creating Symlink ```$ ln -s source_file symbolic_link```
 - list of port - ```$ lsof -i -P -n```
 - get port usage - ```$ lsof -i :<PORT_NUMBER>```
 - updating permissions of a file/dir - ```$ chmod u=rwx,g=rwx,o=rwx myfile``` - u (user), g (group), o (other), r (read), w (write), x (execute)
 - changing the owner/group of a file/dir = ```$ chown user1:group1 myfile```
 - get memory you have - ```$ free -g -h -t```
 - transfer file to other user: ```$ scp -P 3832 <FILE_NAME> <USERNAME>:/home/dev```
 - get load average: ```$ uptime ``` - system load averages for the past 1, 5, and 15 minutes
 - copy files to remote directory with *rsync*: ```$ rsync -av --partial --inplace --append --exclude 'logs' IP_ADRESS:/path/to/remote/directory/ .```
   - -a, --archive: Preserves file attributes, permissions, ownership, and timestamps during synchronization.
   - -v, --verbose: Displays detailed output, providing information about the transferred files.
   - --partial: Keeps partially transferred files if the synchronization process is interrupted.
   - --inplace: Updates files in place on the destination system instead of using temporary files.
   - --append: Appends changes to existing files if they already exist.
   - --exclude 'logs': Ignores the "logs" directory during synchronization. (to ignore multiple: just add more --exclude)
   - .: Destination directory on the local system where files from the source directory will be synchronized (current working directory).
   - __Optional__: --password-file=password.txt when need to use password for remote access
 
#### Search
 - find file in a folder ```$ sudo find <DIRECTORY> -name "<PATTERN>"```
 - search text in directory ```$ grep -rnw DIRECTORY_PATH -e 'TEXT_TO_SEARCH'``` - r (recursive) n (line number) w (whole word)
 - search text in a file ```$ grep <TEXT_TO_SEARCH>  <FILE_NAME>```
 - to exclude a directory using grep ```$ grep -rnw --exclude-dir=EXCLUDED_DIR DIRECTORY_PATH -e 'TEXT_TO_SEARCH' ```
 
#### Count
 - count the number of lines in an command output ```$ <COMMAND> | wc -l```
 - count the number of characters in a file ```$ wc -m yourTextFile```
 - count the number of words in a file ```$ wc -w yourTextFile```
 - count the number of lines in a file ```$ wc -l yourTextFile```

## Git
 - checkout existing branch ```$ git checkout <BARNCH_NAME>``` OR ```$git switch <BARNCH_NAME>``` (git >= 2.23)
 - creating new branch ```$ git checkout -b <BARNCH_NAME>``` OR ```$ git switch -c <BARNCH_NAME>``` (git >= 2.23)
 - commit with message ```$ git commit -m "<MESSAGE>" ```
 - removing all unstaged changes ```$ git checkout -- .```
 - diff with local ```$ git diff <FILE_PATH>```
 - push to remote ```$ git push --set-upstream origin <BRANCH_NAME>``` (as of git v.37.1 you can just ```$ git push```)
 - show commit changes - ```$ git show <SHA>```
 - delete branch locally ```$ git branch -D <BRANCH_NAME>```
 - remove commit locally ```$ git reset HEAD^ ```
 - rename the current branch ```$ git branch -m <NEW_NAME>```
 - discard changes from unstaged file ```$ git restore <FILE_PATH> ``` (git >= 2.23)
#### Stashing
 - stash changes ```$ git stash```
 - list of stashes ```$ git stash list```
 - apply last stash ```$ git stash apply stash@{0}```
 - apply and remove last stash ```$ git stash pop```
#### Cherry pick
 - apply cherry-pick ```$ git cherry-pick <COMMIT-SHA>```
 - abort last cherry-pick ```$ git cherry-pick --abort```
#### Config
 - list global git config ```$ git config --list```
#### Nice Logging
 - tree ```$ git log --graph --pretty="%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(yellow)- %an%C(reset)%C(red)%d%C(reset)"```
 - oneline ```$ git log --oneline --decorate --color --pretty="%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(yellow)- %an%C(reset)%C(red)%d%C(reset)"```
 - with extra info ```$ git log --graph --decorate --all```

## K8S
 - delete namespace - ```$ kubectl delete namespaces <NAMESPACE>```
 - get namespace pods: ```$ kubectl get pods -n <NAMESPACE>```
 - get all cluster/context namespaces: ```$ kubectl get namespaces```
 - information about a pod: ```$ kubectl describe <POD> -n <NAMESPACE>```
 - port forward pod - ```$ kubectl -n <NAMESPACE> port-forward <POD_NAME> <PORT>```
 - get inside a pod - ```$ kubectl -n <NAMESPACE> exec -it <POD_NAME> bash```
 - get inside a container that inside a pod: ```$ kubectl -n <NAMESPACE> exec -it <POD>  -c <Container> bash```
 - delete pod: ```$ kubectl -n <NAMESPACE> delete pod <POD_NAME>```
 - force delete pod: ```$ kubectl -n <NAMESPACE> delete pod <POD_NAME> --grace-period=0 --force```
 - get all NOT running pods: ```$ kubectl  get pods -n <NAMESPACE> | awk '{ if ($3 != "Running"){print} }'```
 - get Service configmap  ```$ kubectl  -n <NAMESPACE> get cm -o yaml```
 - get current context ```$ kubectl config current-context```
 - switch context ```$ kubectl config use-context <CLUSTER_NAME>```
 - show config ```$ kubectl config view```
 - logging a pod ```$ kubectl -n <NAMESPACE> logs -f  <POD_NAME> [-c CONTAINER_NAME] --tail 1000```
 - logging a service ```$ kubectl -n <NAMESPACE> logs -f svc/<SERVICE_NAME> --tail 1000``` - if the service has multiple pods
#### Helm 
 - get list of helm versions: ```$ helm -n <NAMESPACE> list```
 - getting the yaml output of chart: ```$ helm dependencies update <PATH_TO_CART_YAML_FOLDER> && helm template <PATH_TO_CART_YAML_FOLDER>```

## Docker
 - list all working containers ```$ docker container ls```
 - list all existing containers ```$ docker container ls -a```
 - removing all containers ```$ docker rm -f $(docker ps -a -q)```
 - removing all images ```$ docker rmi $(docker images -q)```
 
## VIM [help files](https://vimhelp.org/)
 - open new tab - ```:tabnew```
 - open new window - ```:new```
 - open new vertical window - ```:vnew```
 - navigate between tabs - ```gt``` OR ```gT```
 - close all windows - ```:qall```
 - go to line ```:<LINE_NUMBER> ```
 - move current line down ```:m+ ```
 - move current line up ```:m-2 ```
 - run last command ```@: ```
 - moving lines up or down [link](https://vim.fandom.com/wiki/Moving_lines_up_or_down)
 - copy and paste a line ``` yyp ``` [link](https://www.vimfromscratch.com/articles/how-to-copy-and-paste-a-line-in-vim)
 - delete a line - press on the keyboard ```dd```
 - run terminal command ```:! <COMMAND> ```
 - go to back directory browsing after opening file in vim ```:b#```
 - empty a file: first go to the start of the file with ```gg``` and then delete all lines with ```dG``` 
 - gg - go to first line
 - G - go to last line
 - w - move the cursor forward one word
 - b - moves backward to the start of the previous word
 - x - delete forward chracter
 - X - delete backward character
 - r{char} - Replace the character under the cursor with {char}
 - gUU - Make current line uppercase
 - guu - Make current line lowercase
 - R - Enter Replace mode: Each character you type replaces an existing character
