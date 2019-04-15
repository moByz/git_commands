# git_commands

## https://githowto.com/ru

## Полезные команды

``
git log --pretty=oneline - однострочный просмотр изменений

cat файл - просмотреть содержимое файла
``

## Снять индексацию с проиндексированного файла
``
git reset файл - снять индексацию с add файла

git reset HEAD файл - снять индексацию с add файла, но не измененяет рабочий каталог. Чтобы удалить нежелательные изменения нужно сделать git checkout файл
``

## Алиасы

``
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short" - алиас для просмотра истории

git config --global alias.go checkout - алиас checkout
``


## Теги

``
git tag - просмотреть доступные теги

git hist master --all -просмотреть теги в коммитах

git tag v1 - создание тега версии

git tag v1^ - переход к предыдущей версии
``

## Откат последнего изменения в файле

``
git checkout файл - откат последнего изменения в файле

git revert HEAD --no-edit - откат на предыдущий коммит без открытия в редакторе

git reset --hard к чему откат(хеш коммита, тег) - откат к нужному коммиту либо тегу

git tag -d tag name - удаление тега (вместе с ним потруться все коммиты, которые в нем были) 

git commit --amend -m "commit" - изменение предыдущего коммита, если забыл что-то добавить, чтобы обойтись одним коммитом
``

## Спрятать изменения

``
git stash - спрятать изменения

git stash apply - показать спрятаные изменения
``

https://githowto.com/ru/git_internals_working_directly_with_git_objects
