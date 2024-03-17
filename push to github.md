## 1、基本的推送  

```shell
git add .
git commit -m "提示词"
git remote add origin http://github.com/...
git push origin main
```

## 2、解决 master分支和main分支不匹配问题

1.先给本地分支master改名

```
$ git branch -M main 
```

说明：“-M”对分支重命名

2.查看所有分支

```shell
$ git branch -a
```

```
 main   
	remotes/origin/main   
	remotes/origin/master  
```

3.删除远程分支master

```shell
$ git push origin --delete master 
```

```
To https://github.com/***/learnOpenGL.git

[deleted]         master  
```

4.确认删除情况

```shell
$ git branch -a
```

```
main   
remotes/origin/main  
```

5.切换到当前分支main，也就要保留下来的分支

```shell
$ git checkout main 
```

```
Already on 'main'  
```

说明：“Already on 'main'”已经说明在当前分支

6.合并分支

```shell
$ git merge remotes/origin/main 
```

fatal: refusing to merge unrelated histories 
说明：拒绝合并，需要忽略这个限制，添加“--allow-unrelated-histories”

```
$ git merge remotes/origin/main --allow-unrelated-histories 
```

Merge made by the 'recursive' strategy. 
7.提交修改

```shell
$ git push origin main 
```

```
Enumerating objects: 34, done. 
Counting objects: 100% (34/34), done. 
Delta compression using up to 8 threads 
Compressing objects: 100% (28/28), done. 
Writing objects: 100% (32/32), 1.46 MiB | 1.03 MiB/s, done. 
Total 32 (delta 1), reused 0 (delta 0), pack-reused 0 
remote: Resolving deltas: 100% (1/1), done. 
To https://github.com/test/learnOpenGL.git 
   76a2889..d34cf75  main -> main  
```

8.再次查看分支情况

```
$ git branch -a 
```

```
main   
remotes/origin/main 
```

