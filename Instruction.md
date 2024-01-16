# Подсказки по GIT
## Создание репозитория
Подключение Git к репозиторию и создание в нем скрытой папки *.git*.
```sh
git init
```
## Добавление изменений в Git.
Добавление измененного файла в контроль версий.
```sh
git add
```
## Добавление комментария в Git.
Добавление комментария об изменениях в файле. Обычно пишется на английском.
```sh
git commit -m "Messege text"
```
## Проверка состояния Git.
Проверка текущего состояния папки, контролируемой Git. Выыодятся как сохраненные в Git файлы, так и не добавленные, и не откоммиченные.
```sh
git status
```
## История изменений в Git.
Показывает истроию изменений файлов в контролируемой папке. В порядке от позднего наверху, до раннего внизу.
```sh
git log
```
Для вызова истории без подробностей, а только с комментариями по изменениям добавлем *--oneline*
```sh
git log --oneline
```
Для вызова истории со всеми ветками используем *--graph*
```sh
git log --graph
```
Доп команды можно комбинировать:
```sh
git log --oneline --graph
```
## Работа с ветками
Для вызова списка веток используем команду
```sh
git branch
```
Перемещение между ветками и сохранениями:
```sh
git checkout <имя_ветки_или_коммита> 
```
Создание новой ветки
```sh
git branch <name>
```
Удаление ветки
```sh
git branch -d <name>
```
## Неотслеживаемые файлы
Для того, чтобы файлы (например картинки), не отслеживались Git, создаем файл **_.gitignore_**. И в нем прописываем полное название нужного файла.

## Работа с удаленными репозиториями
Работа с удаленными репозиториями осуществляется с помощью сервиса [github](https://github.com/).

Первым делом создаем копию папки из сервиса (на примере текщего залдания):
```sh
git clone https://github.com/AlexandraProtasenya/SCV_GitPR.git
```

Для передачи данных между локальным и удаленным репозиториями используются две основные команды:
```sh
git pull
```
Выгружает данныес с удаленного на локальные репозиторий и выполняет *merge* с текущим состоянием.
```sh
git push
```
Отправляет данные с локального на удаленный репозиторий.

Для получения информации об удаленном репозитории используем команду
```sh
git remote -v
```
или для более подробной информации
```sh
git remote origin
```

Для отправки на удаленный репозиторий изменений с новой веткой name используем
```sh
git push --set-upstream origin name
```

Для отправки данных на удаленный репозиторий с удалением ветки name используем команду

```sh
git push origin --delete name
```

Или просто удаляем ветку на самом сервисе.

В случае конфликта данных между локальным и удаленным репозиториями мы не сможем отправить данные через push. Для разрешения конфликта сперва выгружаем данные на локальный репозиторий с помощью команды
```sh
git pull rebase
```
Затем исправляем файл локально. Для продолжения работы используем команду
```sh
git rebase --continue
```
И после сохранения и коммита всех изменений отправляем данные на удаленный репозиторий.

## Функция *fork* на сервисе github.com 

Для работы с открытыми проектами часто используется функция *fork*.

Открываем необходимый репозиторий другого пользоваетля (не свой). Нажимаем кнопку fork. Репозиторий копируется на наш аккаунт. 

После этого клонируем его на свой локальный репозиторий. Создаем новую ветку и через нее редактируем проект.

Выгружаем на свой аккаунт измененный репозиторий с новой веткой.

Отправляем запрос на добавление наших правок с помощью функции сервиса pull request.