git init - в выбранном каталоге генерирует новый гит-проект.
git status - пробегается и определяет статус, какие файлы модифицированны/закоммичены, а какие - нет. git status -s - минимальный вывод.
git add "файл" - добавляет файл к отслеживанию. 
Игнорировать файлы можно при помощи файла .gitignore. - принимает любые регулярки с новой строки.
Также пример:
# Исключить все файлы с расширением .a
*.a

# Но отслеживать файл lib.a даже если он подпадает под исключение выше
!lib.a

# Исключить файл TODO в корневом каталоге, но не файл в subdir/TODO
/TODO

# Игнорировать все файлы в каталоге build/
build/

# Игнорировать файл doc/notes.txt, но не файл doc/server/arch.txt
doc/*.txt

# Игнорировать все .txt файлы в каталоге doc/
doc/**/*.txt

git diff - подробный вывод фактических изменений в файлах
git rm 'file' - УДАЛЯЕТ ФАЙЛ ВПРИНЦИПЕ.  git rm --cached 'file' - чтобы не удалять файл из каталога, а только индекс. Можно передавать целый каталог
git mv 'file' - стандарт перемещение
git checkout -f branch - отмена локальных изменений для последующего прыжка.
git checkout (номер версии sha 1 id) - смена версии по комиту
git checkout 'branch' - прыжок на нужную ветку
it checkout -- CONTRIBUTING.md - откат изменения в файле
git commit -m "Story 182: fix benchmarks for speed" - коммит с записью. -a - добавление всех изменений автоматически
git commit --amend - поменять название последнего commit, а также зальются новые отслеживаемые изменения.
git switch -     - откатывает изменения, если HEAD detached at.
git restore 'file' - откатывет изменения в файле

-------------------Теги--------------------
git tag - просмотр имеющихся тегов
git tag -l "v1.8.5*" - поиск по тегу
Аннотированные теги пример создания:
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4

git show <tag> - для его проверки

Легковесные теги
Создание - git tag <v1.4-l>

Можно пометить тегом старые коммиты:
git tag -a v1.2 9fceb02 (последнее - это контрольная сумма коммита или его часть)

git не отправляет теги. Их нужно запушить:
git push origin <tagname>
Или для отправки сразу множества:
git push origin --tags

git tag -d <tagname> - удаление тегов
git checkout v2.0.0 - переход на тег. Однако это создаст detached HEAD. 
--------------------------------
Псевдонимы
git config --global alias.ci commit - пример настройки. вместо ввода git commit, вам достаточно набрать только git ci



-----------------------------------
git branch testing - создание новой ветки
Как Git определяет, в какой ветке вы находитесь? Он хранит специальный указатель HEAD. 
Имейте ввиду, что в Git концепция HEAD значительно отличается от других систем контроля версий,
В Git—это указатель на текущую локальную ветку.
git branch -v - последний коммит в каждой ветке
git branch --move bad-branch-name corrected-branch-name - переименование ветки
git push --set-upstream origin corrected-branch-name - отправление нового имени ветки в репозиторий
git push origin --delete bad-branch-name - удалить старую ветку
git log --all - вся история по веткам
git log --oneline --decorate --graph --all - прикольная штука, визуализация


---------------------merge-----------------------------
git merge hotfix - слить активную ветку с указанной веткой, в данном случае hotfix.
git branch -d hotfix - удалить ветку
Конфликты:
git merge --abort - отмена процедуры слияния в случае коммитов.
git merge --continue - продолжить слияние, если всё ок. Либо просто новый коммит можно создать.
git mergetool - инструмент для слияния (вим-какашка)


-------------------Удалённые репозитории---------------

git remote - просмотр удалённых репозиториев
git remote add origin https://github.com/paulboone/ticgit - добавление в удалённый репозиторий
git fetch [remote-name] - получение изменений в удалённом репозитории
git push origin master - отправка изменений
git push origin --all - запушить сразу все ветки.
git remote show <remote> - просмотр уд. репоз.
git remote rename pb 'rep' - переименовывание репа
git remote remove 'rep' - удаление репозитория
git fetch origin - получить изменения с сервера, информацию о текущих коммитах и т.п. Но не добавляет их. Создаёт ветки слежения.
git fetch --all - все изменения.
git pull
git push origin --delete 'branch' - удаление ветки на сервере

получение репозитория, пример:
git remote add origin git@github.com:DmitrySem7/cuddly-doodle.git
git branch -M main
git push -u origin main