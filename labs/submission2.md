PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git log --oneline -1
f8d938f (HEAD -> feature/lab2) Add test file
938f
tree 7af0d0bb9f47f40a2e789b02b346da1afaab59ad
parent d7b6a663bfa4a9b5183957f04650fdde3f90a2c8
author David Serafimov <surikatser@mail.ru> 1770929106 +0300
committer David Serafimov <surikatser@mail.ru> 1770929106 +0300        
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAg/8ozl8CO7bUApb0evZe1EeAP/Z AAAAQOdg+zHD7xDTXHOW8i6R2KL6VtXy0jurOiqkuw9kbSKM8gTrS6uPirGz+KuXndH3IV 8byatFK3qUseE+dwG0uQg=

Add test file
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git cat-file -p 7af0d0bb9f47f40a2e789b02b346da1afaab59ad
040000 tree 44d77d1e28f407596fc7b49b5da5dd924dbe02be    .github        
100644 blob 6e60bebec0724892a7c82c52183d0a7b467cb6bb    README.md      
040000 tree a1061247fd38ef2a568735939f86af7b1000f83c    app
040000 tree eb79e5a468ab89b024bd4f3ed867c6a3954fe1f0    labs
040000 tree d3fb3722b7a867a83efde73c57c49b5ab3e62c63    lectures       
100644 blob 418a98ced2ac70b5bdee0be9732ecdaae7264515    test.txt       
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git cat-file -p  418a98ced2ac70b5bdee0be9732ecdaae7264515
 ■Test content
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git cat-file -p f8d938f
tree 7af0d0bb9f47f40a2e789b02b346da1afaab59ad
parent d7b6a663bfa4a9b5183957f04650fdde3f90a2c8
author David Serafimov <surikatser@mail.ru> 1770929106 +0300
committer David Serafimov <surikatser@mail.ru> 1770929106 +0300        
gpgsig -----BEGIN SSH SIGNATURE-----
 U1NIU0lHAAAAAQAAADMAAAALc3NoLWVkMjU1MTkAAAAg/8ozl8CO7bUApb0evZe1EeAP/Z gF4xi5Pq/RZ/u8krMAAAADZ2l0AAAAAAAAAAZzaGE1MTIAAABTAAAAC3NzaC1lZDI1NTE5 AAAAQOdg+zHD7xDTXHOW8i6R2KL6VtXy0jurOiqkuw9kbSKM8gTrS6uPirGz+KuXndH3IV 8byatFK3qUseE+dwG0uQg=
 -----END SSH SIGNATURE-----

Add test file
```
Типы объектов:
Blob означает только данные файла. Внутри нет ни пути, ни имени файла.
Tree означает структуру каталогов в один конкретный момент. Он хранит имена, режимы и хэши файлов/подкаталогов.
Commit означает сохранённый снимок проекта с метаданными. Он связывает текущее дерево с предыдущим(и) коммитом(ами).

Как Git хранит данные репозитория:
Git построен на хэшах содержимого: каждый объект получает ID из своего содержимого.
Коммит не хранит все файлы напрямую; он ссылается на tree, а tree ссылается на blob’ы.
Благодаря этой модели Git может безопасно отслеживать историю и быстро восстанавливать старые состояния.

Пример содержимого объектов:
blob:
Hello Git

tree:
1...... blob a..... README.md
1...... blob e..... test.txt

commit:
tree 9a........
parent 1a.......
author Davis Serafimov surikatser@mail.ru

17........ +0300
committer Davis Serafimov surikatser@mail.ru

1......... +0300
```










--------------------------------------------------------------------------------------------




PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git switch -c git-reset-practice
>> "First commit"  | Out-File -Encoding utf8 file.txt
>> git add file.txt
>> 
>> "Second commit" | Add-Content file.txt
>> git add file.txt
>> git commit -m "Second commit"
>> 
>> "Third commit"  | Add-Content file.txt
>> git add file.txt
>> git commit -m "Third commit"
>> 
   ird commit"  | Add-Content file.txt\x0agit add file.txt\x0agit commiSwitched to a new branch 'git-reset-practice'c7-d1ddb6af0e62
[git-reset-practice f5a79ed] First commit
 create mode 100644 file.txt
[git-reset-practice ffd0682] Second commit
 1 file changed, 1 insertion(+)
[git-reset-practice 73de61f] Third commit
 1 file changed, 1 insertion(+)
>> git status
>>
73de61f (HEAD -> git-reset-practice) Third commit
ffd0682 Second commit
f5a79ed First commit
nothing to commit, working tree clean
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git reset --soft HEAD~1
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git status
Changes to be committed:
        modified:   file.txt

ffd0682 (HEAD -> git-reset-practice) Second commit
f5a79ed First commit
46f458d (origin/feature/lab2, feature/lab2) Tast 1 complete
HEAD is now at f5a79ed First commit
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git status
On branch git-reset-practice
nothing to commit, working tree clean
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git log --oneline -3
f5a79ed (HEAD -> git-reset-practice) First commit
46f458d (origin/feature/lab2, feature/lab2) Tast 1 complete
f8d938f Add test file
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git reflog
f5a79ed (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
ffd0682 HEAD@{1}: reset: moving to HEAD~1
73de61f HEAD@{2}: commit: Third commit
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
46f458d (origin/feature/lab2, feature/lab2) HEAD@{6}: commit: Tast 1 complete
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
f5a79ed (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
ffd0682 HEAD@{1}: reset: moving to HEAD~1
73de61f HEAD@{2}: commit: Third commit
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
46f458d (origin/feature/lab2, feature/lab2) HEAD@{6}: commit: Tast 1 complete
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
4dacaec (origin/feature/lab1, feature/lab1) HEAD@{10}: commit: docs: complete lab1 submission
347e452 HEAD@{11}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{12}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{13}: commit: docs: added scrinshots
d2de4a6 HEAD@{14}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{15}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{16}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{17}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{18}: reset: moving to origin/feature/lab1
d2de4a6 HEAD@{19}: checkout: moving from main to feature/lab1
f5a79ed (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
ffd0682 HEAD@{1}: reset: moving to HEAD~1
73de61f HEAD@{2}: commit: Third commit
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
46f458d (origin/feature/lab2, feature/lab2) HEAD@{6}: commit: Tast 1 complete
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
4dacaec (origin/feature/lab1, feature/lab1) HEAD@{10}: commit: docs: complete lab1 submission
347e452 HEAD@{11}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{12}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{13}: commit: docs: added scrinshots
d2de4a6 HEAD@{14}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{15}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{16}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{17}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{18}: reset: moving to origin/feature/lab1
d2de4a6 HEAD@{19}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{20}: commit: chore: add PR template
d6b6a03 HEAD@{21}: reset: moving to origin/main
d6b6a03 HEAD@{22}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{23}: reset: moving to HEAD~1
8f6ed9f HEAD@{24}: commit: chore: add PR template
f5a79ed (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
ffd0682 HEAD@{1}: reset: moving to HEAD~1
73de61f HEAD@{2}: commit: Third commit
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
46f458d (origin/feature/lab2, feature/lab2) HEAD@{6}: commit: Tast 1 complete
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
4dacaec (origin/feature/lab1, feature/lab1) HEAD@{10}: commit: docs: complete lab1 submission
347e452 HEAD@{11}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{12}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{13}: commit: docs: added scrinshots
d2de4a6 HEAD@{14}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{15}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{16}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{17}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{18}: reset: moving to origin/feature/lab1
d2de4a6 HEAD@{19}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{20}: commit: chore: add PR template
d6b6a03 HEAD@{21}: reset: moving to origin/main
d6b6a03 HEAD@{22}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{23}: reset: moving to HEAD~1
8f6ed9f HEAD@{24}: commit: chore: add PR template
f5a79ed (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
ffd0682 HEAD@{1}: reset: moving to HEAD~1
73de61f HEAD@{2}: commit: Third commit
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
46f458d (origin/feature/lab2, feature/lab2) HEAD@{6}: commit: Tast 1 complete
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
4dacaec (origin/feature/lab1, feature/lab1) HEAD@{10}: commit: docs: complete lab1 submission
347e452 HEAD@{11}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{12}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{13}: commit: docs: added scrinshots
d2de4a6 HEAD@{14}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{15}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{16}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{17}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{18}: reset: moving to origin/feature/lab1
d2de4a6 HEAD@{19}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{20}: commit: chore: add PR template
d6b6a03 HEAD@{21}: reset: moving to origin/main
d6b6a03 HEAD@{22}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{23}: reset: moving to HEAD~1
f5a79ed (HEAD -> git-reset-practice) HEAD@{0}: reset: moving to HEAD~1
ffd0682 HEAD@{1}: reset: moving to HEAD~1
73de61f HEAD@{2}: commit: Third commit
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
46f458d (origin/feature/lab2, feature/lab2) HEAD@{6}: commit: Tast 1 complete
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
4dacaec (origin/feature/lab1, feature/lab1) HEAD@{10}: commit: docs: complete lab1 submission
347e452 HEAD@{11}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{12}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{13}: commit: docs: added scrinshots
d2de4a6 HEAD@{14}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{15}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{16}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{17}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{18}: reset: moving to origin/feature/lab1
d2de4a6 HEAD@{19}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{20}: commit: chore: add PR template
d6b6a03 HEAD@{21}: reset: moving to origin/main
d6b6a03 HEAD@{22}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{23}: reset: moving to HEAD~1
8f6ed9f HEAD@{24}: commit: chore: add PR template
d2de4a6 HEAD@{25}: commit: docs: add lab1 submission stub
d6b6a03 HEAD@{26}: checkout: moving from main to feature/lab1
d6b6a03 HEAD@{27}: reset: moving to origin/main
d6b6a03 HEAD@{28}: checkout: moving from main to main
d6b6a03 HEAD@{29}: clone: from https://github.com/Milterr/DevOps-Intro.git
~
~
~
~
~
(END)...skipping...
ffd0682 HEAD@{1}: reset: moving to HEAD~1
ffd0682 HEAD@{3}: commit: Second commit
f5a79ed (HEAD -> git-reset-practice) HEAD@{4}: commit: First commit
46f458d (origin/feature/lab2, feature/lab2) HEAD@{5}: checkout: moving from feature/lab2 to git-reset-practice   
f8d938f HEAD@{7}: commit: Add test file
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{8}: checkout: moving from main to feature/lab2
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{9}: checkout: moving from feature/lab1 to main
4dacaec (origin/feature/lab1, feature/lab1) HEAD@{10}: commit: docs: complete lab1 submission
347e452 HEAD@{11}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{12}: checkout: moving from feature/lab1 to feature/lab1
347e452 HEAD@{13}: commit: docs: added scrinshots
d2de4a6 HEAD@{14}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{15}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{16}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{17}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{18}: reset: moving to origin/feature/lab1
d2de4a6 HEAD@{19}: checkout: moving from main to feature/lab1
d7b6a66 (origin/main, origin/HEAD, main) HEAD@{20}: commit: chore: add PR template
d6b6a03 HEAD@{21}: reset: moving to origin/main
d6b6a03 HEAD@{22}: checkout: moving from feature/lab1 to main
d2de4a6 HEAD@{23}: reset: moving to HEAD~1
8f6ed9f HEAD@{24}: commit: chore: add PR template
d2de4a6 HEAD@{25}: commit: docs: add lab1 submission stub
d6b6a03 HEAD@{26}: checkout: moving from main to feature/lab1
d6b6a03 HEAD@{27}: reset: moving to origin/main
d6b6a03 HEAD@{28}: checkout: moving from main to main
d6b6a03 HEAD@{29}: clone: from https://github.com/Milterr/DevOps-Intro.git
~
~
~
~
~
~
~
~
~
~
~
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git reset --hard 73de61f 
HEAD is now at 73de61f Third commit
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git log --oneline -3
73de61f (HEAD -> git-reset-practice) Third commit
ffd0682 Second commit
f5a79ed First commit
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git switch feature/lab2
Switched to branch 'feature/lab2'
Your branch is up to date with 'origin/feature/lab2'.
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro>


```
Я выполнил процедуру reset в отдельной ветке, чтобы проверить изменения истории без риска для основной лабораторной ветки.
Soft reset удалил последний коммит из истории, но оставил его изменения файлов в staged-состоянии.
Hard reset удалил следующий коммит и очистил как индекс, так и рабочее дерево.
С помощью reflog я нашёл хеш удалённого «Third commit» (73de61f) и восстановил состояние ветки.
Все выводы команд приведены выше, поэтому этот раздел сосредоточен на интерпретации.
Ключевой вывод прост: reset может переписывать локальную историю, но reflog позволяет восстановить предыдущие состояния HEAD.
```
























PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git switch -c side-branch
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> echo "Branch commit" >> history.txt
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git add history.txt
[side-branch d3081bb] Side branch commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 history.txt
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git switch -
Switched to branch 'feature/lab2'
Your branch is up to date with 'origin/feature/lab2'.
PS C:\Users\David\PycharmProjects\INT\DevOps-Intro> git log --oneline --graph --all
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
| * 73de61f (git-reset-practice) Third commit
| * ffd0682 Second commit
| * f5a79ed First commit
|/
* 46f458d Tast 1 complete
* f8d938f Add test file
* d7b6a66 (origin/main, origin/HEAD, main) chore: add PR template
| * 4dacaec (origin/feature/lab1, feature/lab1) docs: complete lab1 submission
| * 347e452 docs: added scrinshots
| * d2de4a6 docs: add lab1 submission stub
|/
* d6b6a03 Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
| * 73de61f (git-reset-practice) Third commit
| * ffd0682 Second commit
| * f5a79ed First commit
|/
* 46f458d Tast 1 complete
* f8d938f Add test file
* d7b6a66 (origin/main, origin/HEAD, main) chore: add PR template
| * 4dacaec (origin/feature/lab1, feature/lab1) docs: complete lab1 submission
| * 347e452 docs: added scrinshots
| * d2de4a6 docs: add lab1 submission stub
|/
* d6b6a03 Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
* 1e1c32b feat: update structure
* 6c27ee7 feat: publish lecs 9 & 10
* 1826c36 feat: update lab7
* 3049f08 feat: publish lec8
* da8f635 feat: introduce all labs and revised structure
* 04b174e feat: publish lab and lec #5
* 67f12f1 feat: publish labs 4&5, revise others
* 82d1989 feat: publish lab3 and lec3
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
| * 73de61f (git-reset-practice) Third commit
| * ffd0682 Second commit
| * f5a79ed First commit
|/
* 46f458d Tast 1 complete
* f8d938f Add test file
* d7b6a66 (origin/main, origin/HEAD, main) chore: add PR template
| * 4dacaec (origin/feature/lab1, feature/lab1) docs: complete lab1 submission
| * 347e452 docs: added scrinshots
| * d2de4a6 docs: add lab1 submission stub
|/
* d6b6a03 Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
* 1e1c32b feat: update structure
* 6c27ee7 feat: publish lecs 9 & 10
* 1826c36 feat: update lab7
* 3049f08 feat: publish lec8
* da8f635 feat: introduce all labs and revised structure
* 04b174e feat: publish lab and lec #5
* 67f12f1 feat: publish labs 4&5, revise others
* 82d1989 feat: publish lab3 and lec3
* 3f80c83 feat: publish lec2
* 499f2ba feat: publish lab2
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
| * 73de61f (git-reset-practice) Third commit
| * ffd0682 Second commit
| * f5a79ed First commit
|/
* 46f458d Tast 1 complete
* f8d938f Add test file
* d7b6a66 (origin/main, origin/HEAD, main) chore: add PR template
| * 4dacaec (origin/feature/lab1, feature/lab1) docs: complete lab1 submission
| * 347e452 docs: added scrinshots
| * d2de4a6 docs: add lab1 submission stub
|/
* d6b6a03 Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
* 1e1c32b feat: update structure
* 6c27ee7 feat: publish lecs 9 & 10
* 1826c36 feat: update lab7
* 3049f08 feat: publish lec8
* da8f635 feat: introduce all labs and revised structure
* 04b174e feat: publish lab and lec #5
* 67f12f1 feat: publish labs 4&5, revise others
* 82d1989 feat: publish lab3 and lec3
* 3f80c83 feat: publish lec2
* 499f2ba feat: publish lab2
* af0da89 feat: update lab1
* 74a8c27 Publish lab1
* f0485c0 Publish lec1
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
| * 73de61f (git-reset-practice) Third commit
| * ffd0682 Second commit
| * f5a79ed First commit
|/
* 46f458d Tast 1 complete
* f8d938f Add test file
* d7b6a66 (origin/main, origin/HEAD, main) chore: add PR template
| * 4dacaec (origin/feature/lab1, feature/lab1) docs: complete lab1 submission
| * 347e452 docs: added scrinshots
| * d2de4a6 docs: add lab1 submission stub
|/
* d6b6a03 Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
* 1e1c32b feat: update structure
* 6c27ee7 feat: publish lecs 9 & 10
* 1826c36 feat: update lab7
* 3049f08 feat: publish lec8
* da8f635 feat: introduce all labs and revised structure
* 04b174e feat: publish lab and lec #5
* 67f12f1 feat: publish labs 4&5, revise others
* 82d1989 feat: publish lab3 and lec3
* 3f80c83 feat: publish lec2
* 499f2ba feat: publish lab2
* af0da89 feat: update lab1
* 74a8c27 Publish lab1
* f0485c0 Publish lec1
* 31dd11b Publish README.md
~
(END)...skipping...
* d3081bb (side-branch) Side branch commit
* e6bab03 (HEAD -> feature/lab2, origin/feature/lab2) Tast 2 complete
| * 73de61f (git-reset-practice) Third commit
| * ffd0682 Second commit
| * f5a79ed First commit
|/
* 46f458d Tast 1 complete
* f8d938f Add test file
* d7b6a66 (origin/main, origin/HEAD, main) chore: add PR template
| * 4dacaec (origin/feature/lab1, feature/lab1) docs: complete lab1 submission
| * 347e452 docs: added scrinshots
| * d2de4a6 docs: add lab1 submission stub
|/
* d6b6a03 Update lab2
* 87810a0 feat: remove old Exam Exemption Policy
* 1e1c32b feat: update structure
* 6c27ee7 feat: publish lecs 9 & 10
* 1826c36 feat: update lab7
* 3049f08 feat: publish lec8
* da8f635 feat: introduce all labs and revised structure
* 04b174e feat: publish lab and lec #5
* 67f12f1 feat: publish labs 4&5, revise others
* 82d1989 feat: publish lab3 and lec3
* 3f80c83 feat: publish lec2
* 499f2ba feat: publish lab2
* af0da89 feat: update lab1
* 74a8c27 Publish lab1
* f0485c0 Publish lec1
* 31dd11b Publish README.md
~
~
(END)


```
Для этого задания я создал ветку side-branch, сделал в ней один коммит, вернулся обратно и проверил историю с помощью:

git log --oneline --graph --all

Фрагмент графа приложен выше. Он наглядно показывает линию ветки и порядок коммитов во всех ветках.

Сообщения коммитов, видимые в графе:
- Side branch commit

Рефлексия:
--graph даёт ясную картину потока ветвления и связей между коммитами.  
Это упрощает отладку и ревью кода, особенно когда
```


























Я создал и отправил (push) релизные теги:

git tag v1.0.0
git push origin v1.0.0

Связанные хеши:
- v1.0.0 -> 594a2baad3d84bec9153719cf32dcfbd3e6e79a9

В моём случае между версиями не было новых коммитов, поэтому оба тега могут указывать на один и тот же коммит.

Почему теги важны:
Теги задают чёткие точки версий в истории Git.
Они помогают с версионированием, триггерами CI/CD и отслеживанием релизов.
