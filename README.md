# Usefull Terminal commands

## Bash

 - running processes ```$ ps aux```
 - kill running processes by pattern ```$ pkill -f <PATTERN>  ```
 - search text in directory ```$ grep -rnw DIRECTORY_PATH -e 'TEXT_TO_SEARCH'``` - r (recursive) n (line number) w (whole word)
 - get my public IP ```$ hostname -I | awk '{print $1}'```
 - view system information using neofetch ```$ neofetch``` 
 - get folder size - ```$ du -hs <FOLDER_NAME>```
 - Creating Symlink ```$ ln -s source_file symbolic_link```
 - list of port - ```$ lsof -i -P -n```

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
### Stashing
 - stash changes ```$ git stash```
 - list of stashes ```$ git stash list```
 - apply last stash ```$ git stash apply stash@{0}```
 - apply and remove last stash ```$ git stash pop```
### Cherry pick
 - apply cherry-pick ```$ git cherry-pick <COMMIT-SHA>```
 - abort last cherry-pick ```$ git cherry-pick --abort```
### Config
 - list global git config ```$ git config --list```
### Nice Logging
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
### Helm 
 - get list of helm versions: ```$ helm -n <NAMESPACE> list```

## Docker
 - list all working containers ```$ docker container ls```
 - list all existing containers ```$ docker container ls -a```
 - removing all containers ```$ docker rm -f $(docker ps -a -q)```
 - removing all images ```$ docker rmi $(docker images -q)```
