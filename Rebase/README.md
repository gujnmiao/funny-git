# rebase
1. 从master切出一个开发分支
```
git checkout -b feature/v1.0.0
git push -u origin feature/v1.0.0
```
2. 修改README.md并提交
```
git add README.md
git commit -m "FEATURE:v1.0.0"
git push origin feature/v1.0.0
```
3. 发现线上代码有严重bug要紧急处理
```
git checkout master
git checkout -b hotfix/202004271558
git add README.md
git commit -m "BUGFIX:202004271558"
git push -u origin hotfix/202004271558
git checkout master
git merge hotfix/202004271558
```
4. 这个时候feature/v1.0.0开发完成
```
git checkout master
git merge feature/v1.0.0
```
由于当前分支已经落后master分支合并的过程中可能会产生冲突
**Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.**
5. 使用rebase变基
```
git rebase master
git add README.md
git commit -m "FEATURE:rebase to master"
git checkout master
git rebase feature/v1.0.0
git pull origin master
```


