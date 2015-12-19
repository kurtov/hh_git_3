```
git init
echo 'В лесу родилась ёлочка,' >> task3.txt
echo 'В лесу она росла.' >> task3.txt
echo 'Зимой и летом стройная,' >> task3.txt
echo 'Зелёная была.' >> task3.txt
git hash-object -w task3.txt
git update-index --add task3.txt
git write-tree #9bb8d61a7db91f6ab32b0f544c5fd3637440351f
echo "commit `git config user.name` 1" | git commit-tree 9bb8d61a7db91f6ab32b0f544c5fd3637440351f #c2957f38fb328708216dd6b87b0390533d3de0b0

echo 'Маленькой елочке' >> task3_new.txt
echo 'Холодно зимой.' >> task3_new.txt
echo 'Метель ей пела песенку:' > task3.txt
echo '"Спи, ёлочка, бай-бай!"' >> task3.txt
echo 'Мороз снежком укутывал:' >> task3.txt
echo '"Смотри, не замерзай!"' >> task3.txt
git hash-object -w task3_new.txt
git hash-object -w task3.txt
git update-index task3.txt
git update-index --add task3_new.txt
git write-tree #2bd460ce87130c58ee8a401d98cb882de64dfb91
echo "commit `git config user.name` 2" | git commit-tree 2bd460ce87130c58ee8a401d98cb882de64dfb91 -p c2957f38fb328708216dd6b87b0390533d3de0b0 #037648b64fbe1c711370790cd68820f89e7f4033

git read-tree --prefix=gittask 9bb8d61a7db91f6ab32b0f544c5fd3637440351f
git write-tree #1dce8057372d1c006428c5a9dbe7b0ec7718667c
echo "commit `git config user.name` 3" | git commit-tree 1dce8057372d1c006428c5a9dbe7b0ec7718667c -p 037648b64fbe1c711370790cd68820f89e7f4033 #df668fbc959be4e69bd3b425879fe875cd3d2877

git update-ref refs/heads/master df668fbc959be4e69bd3b425879fe875cd3d2877
git remote add origin https://github.com/kurtov/hh_git_3.git
git push -u origin master
```

Ссылки:
- https://git-scm.com/book/ru/v1/Git-изнутри-Объекты-в-Git
- https://git-scm.com/book/ru/v1/Git-изнутри-Ссылки-в-Git
