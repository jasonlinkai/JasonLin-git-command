# *常用的git命令* #

### *rebase*  ###
找出共同父節點，並將雙方共同父節點之上之節點進行合併。
節點歷程則將以`TARGET_BRANCH`之`HEAD`作為基點，從`HEAD`插入當前分支之共同父節點之上
的節點。如果合併過程中有衝突，須將其解決，並生成新的提交加至到歷程最頂。
```Shell
git rebase ${TARGET_BRANCH}
```
將`HEAD`與`SHA1`之間的提交分別進行操作。
pick - 使用該次提交內容。
squash - 使用該次提交內容，將內容融入前一個被`pick`的提交。
```Shell
git rebase -i ${SHA1}^
```
- - -

### *reset* ###
將`staged`檔案全退至`unstaged`。
```Shell
git reset HEAD .
```
將`staged`檔案退至`unstaged`。
```Shell
git reset HEAD ${FILE_PATH_1} ${FILE_PATH_2}
```
將`HEAD`到`SHA1`之間的提交撤銷，並將異動`unstaged`。
```Shell
git reset ${SHA1}^
```
以`TARGET_BRANCH`分支內容，覆蓋當前分支。
```Shell
git reset --hard ${TARGET_BRANCH}
```
- - -

### *revert* ###
還原選定提交的修改，並將還原之內容`staged`。
```Shell
git revert --no-commit ${SHA1}
```
還原`SHA1`到`SHA2`內(包含自身)之提交，並將還原之內容`staged`。

```Shell
git revert --no-commit ${SHA1}^..${SHA2}
```
- - -

### *cherry-pick* ###
將某個提交加入當前分支。
```Shell
git cherry-pick ${SHA1}
```
- - -

### *reflog* ###

查看操作歷程，可以回退到那些`SHA`值之狀態。
```Shell
git reflog
```
- - -

### *diff* ###
比對分支之檔案差異。`BRANCH_A`內容以 --- 表示。`BRANCH_B`內容以 +++ 表示。
```Shell
git diff ${BRANCH_A}..${BRANCH_B}
```
- - -

### *merge* ###
合併`TARGET_BRANCH`分支到當前分支，且不快進。
```Shell
git merge --no-ff ${TARGET_BRANCH}
```
- - -

### *checkout* ###
切換分支至`TARGET_BRANCH`分支。
```Shell
git checkout ${TRAGET_BRANCH}
```
以當前分支及狀態切換並建立本地分支。
```Shell
git checkout -b ${TRAGET_BRANCH}
```
將`unstaged`檔案全清除。
```Shell
git checkout .
```
將指定位置的`unstaged`檔案清除。
```Shell
git checkout ${FILE_PATH_1} ${FILE_PATH_2}
```
- - -

### *status* ###
查看當前分支異動狀態。
```Shell
git status
```
- - -

### *lg* ###
查看節點歷程圖。
```Shell
git lg
```
- - -

### *ll* ###

查看節點歷程，能看見有哪些檔案異動及異動行數。
```Shell
git ll
```
- - -

### *fetch* ###
以遠程倉庫所有分支之最新內容，自動更新本地遠程分支內容。
```Shell
git fetch
```
- - -

### *push* ###
將當前分支內容強制複寫至遠程倉庫。
```Shell
git push -f
```
- - -

### *add* ###
將`unstaged`檔案全`staged`。
```Shell
git add .
```
將指定位置的`unstaged`檔案`staged`。
```Shell
git add ${FILE_PATH_1} ${FILE_PATH_2}
```
