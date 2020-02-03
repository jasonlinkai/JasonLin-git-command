# *常用的git命令* #
## 記錄一些工作中常用的git命令。 ##

- - -

### *rebase*  ###
找出"共同父節點"，並將雙方"共同父節點"之上之節點進行合併。
節點歷程則將以"目標分支HEAD"作為基點，從HEAD插入"當前分支"之"共同父節點"之上
的節點。如果合併過程中有衝突，須將其解決，並生成新的commit加至到歷程最頂。

    git rebase ${TARGET_BRANCH}

將HEAD與SHA1之間的commit分別進行操作。
pick - 使用該次commit內容。
squash - 使用該次commit內容，將內容融入前一個被pick的commit。

    git rebase -i ${SHA1}^

- - -

### *reset* ###
將staged檔案全退至unstaged。

    git reset HEAD .

將staged檔案退至unstaged。

    git reset HEAD ${FILE_PATH_1} ${FILE_PATH_2}

將HEAD到"SHA1"之間的commit撤銷，並將異動unstaged。

    git reset ${SHA1}^

以"目標分支"內容，覆蓋"當前分支"。

    git reset --hard ${TARGET_BRANCH}

- - -

### *revert* ###
還原選定commit的修改，並將還原之內容加入暫存區(added)。

    git revert --no-commit ${SHA1}

還原範圍內之commit的修改，並將還原之內容加入暫存區(added)。

    git revert --no-commit ${SHA1}^..${SHA2}

- - -

### *cherry-pick* ###
將某個commit加入當前分支。

    git cherry-pick ${SHA1}

- - -

### *reflog* ###

查看git操作歷程，可以reset到那些SHA值。

    git reflog

- - -

### *diff* ###
比對分支之檔案差異。"A分支"內容以 --- 表示。"B分支"內容以 +++ 表示。

    git diff ${BRANCH_A}..${BRANCH_B}

- - -

### *merge* ###
合併"目標分支"到當前分支，且不快進。

    git merge --no-ff ${TARGET_BRANCH}

- - -

### *checkout* ###
切換分支至"目標分支"。

    git checkout ${TRAGET_BRANCH}

以"當前分支"及狀態切換並建立本地分支。

    git checkout -b ${TRAGET_BRANCH}

將unstaged檔案全清除。

    git checkout .

將指定位置的unstaged檔案清除。

    git checkout ${FILE_PATH_1} ${FILE_PATH_2}

- - -

### *status* ###
查看當前分支異動狀態。

    git status

- - -

### *lg* ###
查看節點歷程圖。

    git lg

- - -

### *ll* ###

查看節點歷程，能看見有哪些檔案異動及異動行數。

    git ll

- - -

### *fetch* ###
以遠程倉庫所有分支之最新內容，自動更新本地遠程分支內容。

    git fetch

- - -

### *push* ###
將"當前分支"內容強制複寫至遠程倉庫。

    git push -f

- - -

### *add* ###
將unstaged檔案全staged。

    git add .

將指定位置的unstaged檔案staged。

    git add ${FILE_PATH_1} ${FILE_PATH_2}
