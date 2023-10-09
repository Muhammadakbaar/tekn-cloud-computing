```
git version
git version 2.30.2
```

```
git config --list
user.email=mohammadakbaar11@gmail.com
user.name=muhammadakbaar
```

```
git clone git@github.com:Muhammadakbaar/awesome-project.git
Cloning into 'awesome-project'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.

       │ File: README.md
───────┼──────────────────────────────────────
   1 ~ │ # My Awesome Project

```

```
git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

```
git add .
```

```
git commit -m "Add: README.md"
[master a9cd3e5] Add: README.md
 1 file changed, 1 insertion(+), 1 deletion(-)
```

```
git push origin master
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 271 bytes | 271.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:Muhammadakbaar/awesome-project.git
   c4f740c..a9cd3e5  master -> master
```