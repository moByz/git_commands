# Система контроля версий Git
## https://githowto.com/ru
## Полезные команды
```
ls - проверить что лежит в папке.
cd путь - переход по нужному пути.
mkdir имя папки - создает папку.
touch имя файла - создает файл.
cat файл - просмотреть содержимое файла.
git rm -r имя директории - удаление директории, при непроиндексированном изменении гит будет ругаться.
git rm -f имя файла - удаляет непроиндексированный файл.
git mv index.html hello.html - переименует файл index.html в hello.html.
```
## Просмотр истрории
```
git log - посмотреть историю.
git log --oneline - однострочный просмотр истории.
git log --all - посмотреть всю историю.
git reflog - выведет историю в данной ветке.
```
## Коммиты
```
git commit -am "commit" - закоммитить все измененные файлы одним коммитом. С этой командой нужно быть осторожнее, чтобы не закоммитить лишнего.
git commit -m "commit" nameFile - создать коммит нужного файла.
```
## Снять индексацию
```
git reset nameFile - снять индексацию с add файла.
git reset HEAD nameFile - снять индексацию с add файла, но не измененяет рабочий каталог. Чтобы удалить нежелательные изменения нужно сделать git checkout файл.
```
## Алиасы
```
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short" - алиас для просмотра истории.
git config --global alias.go checkout - алиас checkout, вместо команды checkout можно теперь использовать go.
```
## Теги
```
git tag nameTag - создать тег.
git tag - просмотреть доступные теги.
git hist master --all - просмотреть теги в коммитах.
git tag nameTag^ - переход к предыдущему тегу.
git tag -d tagName - удаление тега (вместе с ним потруться все коммиты, которые в нем были). 
```
## Откаты
```
git checkout nameFile - откат последнего изменения в файле.
git revert HEAD --no-edit - откат на предыдущий коммит без открытия в редакторе.
```
## Исправление предыдущего коммита
```
git commit --amend -m "commit" - изменение предыдущего коммита (если забыл что-то добавить), чтобы обойтись одним коммитом.
git commit --amend --reset-autor - уберет автора и сделает автором текущего пользователя.
```
## Reset
```
git reset --hard к чему откат (хеш коммита, тег) - откат к нужному коммиту либо тегу.
git reset --keep - оставит изменения в файлах, но убирет незакоммиченные файлы из индекса.
```
## Спрятать изменения
```
git stash - спрятать изменения.
git stash apply - показать спрятаные изменения.
```
## Ветки
```
git branch - посмотреть доступные ветки.
git branch -a - посмотреть все ветки, включая удаленные.
git branch nameBranch - создает ветку.
git checkout -b nameBranch - создать ветку и переключится на нее.
git checkout nameBranch - переключиться на нужную ветку.
git checkout -b myfeature develop - создать ветку myfeature от ветки develop и переключиться на нее.
git branch -d nameBranch - удалить ветку.
```
## Слияние 
```
git merge nameBranch - слить включенную ветку с которой мы хотим, если возникли конфликты необходимо их решить. После решения конфликтов проиндексировать файлы и сделать их коммит.
git merge --no-ff nameBranch - флаг --no-ff вынуждает Git всегда создавать новый объект коммита при слиянии. Это позволяет не терять информацию о том, что ветка существовала, и группирует вместе все внесённые изменения. Таким образом можно отследить какая группа коммитов образует ту или иную функциональность.
```
## Отмена слияния
```
git reset --merge - отменит слияние.
```
## Сброс ветки
```
git reset --hard hashCommit - сбросить ветку к нужному коммиту.
```
## Перебазирование
```
git rebase nameBranch - перебазирует изменения из нужной ветки во включенную. Конечный результат перебазирования очень похож на результат слияния. Однако из нужной ветки прилетят все коммиты.
git rebase --abort - вернет все назад.

Не используйте перебазировние:
1. Если ветка является публичной и расшаренной. Переписывание общих веток будет мешать работе других членов команды.
2. Когда важна точная история коммитов ветки (так как команда rebase переписывает историю коммитов).
```
## Клонирование
```
git clone nameRepos nameClone - сначала нужно от корня репозитория выполнить команду cd .. , далее выполнить команду клонирования.
```
## Удаленные репозитории
```
git remote - узнать об именах удаленных репозиториев.
git branch --track style origin/style - добавить локальную ветку style, которая отслеживает удаленную ветку origin/style.
```
## Получение изменений
```
git fetch - извлекает новые коммиты из удаленного репозитория, но не сливает их с наработками в локальном репозитории.
git merge origin/master - сливает удаленный репозиторий с локальным после извлеченных изменений.
git pull origin master - выполняет сразу две команды git fetch и git merge origin/master.
```
## Чистые репозитории
```
git clone --bare hello hello.git - создает чистый репозиторий директории hello.
git remote add shared ../hello.git - добавление удаленного чистого репозитория к нашему оригинальному.
```
## Отправка изменений 
```
git push origin master - отправка измений в удаленную ветку master.
```
## Копирование коммитов
```
git cherry-pick hashCommit - скопирует коммит.
```
