# 撤销commit但未push的命令
1.找到想要撤销的id 
```git
    git log
```
2.撤销commit

> 撤销,同时将代码恢复到前一commit_id 对应的版本 
```git
git reset –hard id 
```

> 撤销，但是不对代码修改
```git
git reset HEAD^
```