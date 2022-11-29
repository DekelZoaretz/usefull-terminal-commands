# Usefull Terminal commands

## Bash

 - running processes ```$ ps aux```
 - kill running processes by pattern ```$ pkill -f <PATTERN>  ```
 - get my public IP ```$ hostname -I | awk '{print $1}'```
 - view system information using neofetch ```$ neofetch``` 
 - get folder size - ```$ du -hs <FOLDER_NAME>```
 - Creating Symlink ```$ ln -s source_file symbolic_link```
 - list of port - ```$ lsof -i -P -n```
 
#### Search
 - find file in a folder ```$ sudo find <DIRECTORY> -name "<PATTERN>"```
 - search text in directory ```$ grep -rnw DIRECTORY_PATH -e 'TEXT_TO_SEARCH'``` - r (recursive) n (line number) w (whole word)
 - search text in a file ```$ grep <TEXT_TO_SEARCH>  <FILE_NAME>```
 
#### Count
 - count the number of lines in an command output ```$ <COMMAND> | wc -l```
 - count the number of characters in a file ```$ wc -m yourTextFile```
 - count the number of words in a file ```$ wc -w yourTextFile```
 - count the number of lines in a file ```$ wc -l yourTextFile```

## Git
 - checkout existing branch ```$ git checkout <BARNCH_NAME>```
 - commit with message ```$ git commit -m "<MESSAGE>" ```
 - removing all unstaged changes ```$ git checkout -- .```
 - diff with local ```$ git diff <FILE_PATH>```
 - push to remote ```$ git push --set-upstream origin <BRANCH_NAME>``` (as of git v.37.1 you can just ```$ git push```)
 - show commit changes - ```$ git show <SHA>```
 - delete branch locally ```$ git branch -D <BRANCH_NAME>```
 - remove commit locally ```$ git reset HEAD^ ```
 - rename the current branch ```$ git branch -m <NEW_NAME>```
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
 - get all NOT running pods: ```$ kubectl  get pods -n <NAMESPACE> | awk '{ if ($3 != "Running"){print} }'```
 - get Service configmap  ```$ kubectl  -n <NAMESPACE> get cm -o yaml```
 - get current context ```$ kubectl config current-context```
 - switch context ```$ kubectl config use-context <CLUSTER_NAME>```
 - show config ```$ kubectl config view```
#### Helm 
 - get list of helm versions: ```$ helm -n <NAMESPACE> list```

## Docker
 - list all working containers ```$ docker container ls```
 - list all existing containers ```$ docker container ls -a```
 - removing all containers ```$ docker rm -f $(docker ps -a -q)```
 - removing all images ```$ docker rmi $(docker images -q)```
 
## VIM
 - go to line ```:<LINE_NUMBER> ```
 - move current line down ```:m+ ```
 - move cuurent line up ```:m-2 ```
 - run last command ```@: ```
 - moving lines up or down [link](https://vim.fandom.com/wiki/Moving_lines_up_or_down)
 - copy and paste a line  [link](https://www.vimfromscratch.com/articles/how-to-copy-and-paste-a-line-in-vim)
 - delete a line - press on the keyboard ```dd```
 - run terminal command ```:! <COMMAND> ```
 - go to back directory browsing after opening file in vim ```:b#```
 - empty a file: first go to the start of the file with ```gg``` and then delete all lines with ```dG``` 

#### vimrc configuration
```sh
syntax enable
set number
set showcmd
"" set mouse=a
set cursorline
filetype indent on
set wildmenu
set showmatch
set incsearch
set hlsearch

" Auto text wrapping
set wrap

" Encoding
set encoding=utf-8

" Status bar
set laststatus=2

" Intent width
set shiftwidth=2
```
