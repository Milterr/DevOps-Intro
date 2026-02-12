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