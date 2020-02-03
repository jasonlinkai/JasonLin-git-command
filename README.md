# 常用的git命令 #

## revert ##
### git revert --no-commit ${SHA1} ###
```
還原選定commit的修改，並將還原之內容加入暫存區(added)。
```
### git revert --no-commit ${SHA1}^..${SHA2} ###
```
還原範圍內之commit的修改，並將還原之內容加入暫存區(added)。
```

## rebase  ##
### git rebase ${TARGET_BRANCH} ###
```
找出"共同父節點"，並將雙方"共同父節點"之上之節點進行合併(有機會衝突)。節點歷程則將以"目標分支HEAD"作為基點，從HEAD插入"當前分支"之"共同父節點"之上的節點。如果合併過程中有衝突，須將其解決，並生成新的commit加至到歷程最頂。
```

### git rebase -i ${SHA1}^ ###
```
將HEAD與SHA1之commit分別進行操作。
```
* pick - 使用該次commit內容
* squash - 使用該次commit內容，將內容融入前一個被pick的commit


