## Выводы команд в Linux

### Переход в папку

```bash
cd "/home/vboxuser/Рабочий стол/project/projects/ponomaryovmiron_labs"
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Удаление старой папки

```bash
rm -rf lab02hw
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Клонирование репозитория

```bash
git clone https://github.com/ponomaryovmiron/lab02tut.git lab02hw
```

Вывод в Linux:

```text
Cloning into 'lab02hw'...
remote: Enumerating objects...
remote: Counting objects: 100%
remote: Compressing objects: 100%
Receiving objects: 100%
Resolving deltas: 100%
```

---

### Переход в папку lab02hw

```bash
cd lab02hw
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Удаление старого origin

```bash
git remote remove origin
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Добавление нового origin

```bash
git remote add origin https://github.com/ponomaryovmiron/lab02hw.git
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Переименование ветки

```bash
git branch -M main
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Настройка пользователя Git

```bash
git config --global user.name "ponomaryovmiron"
git config --global user.email "godgezuru@gmail.com"
```

Вывод в Linux:

```text
вывод отсутствует
```

---


Вывод в Linux:

```text
вывод отсутствует
```

---

### Компиляция первой версии программы

```bash
g++ hello_world.cpp -o hello_world
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Запуск первой версии программы

```bash
./hello_world
```

Вывод в Linux:

```text
Hello world
```

---

### Удаление исполняемого файла

```bash
rm -f hello_world
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Первый коммит и push

```bash
git add hello_world.cpp
git commit -m "add hello world program"
git push origin main
```

Вывод в Linux:

```text
[main 94ee833] add hello world program
 1 file changed, 8 insertions(+)
 create mode 100644 hello_world.cpp

Enumerating objects...
Counting objects: 100%
Writing objects: 100%
To https://github.com/ponomaryovmiron/lab02hw.git
```

---

### Проверка программы с вводом имени

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Вывод в Linux:

```text
Hello world from @miron
```

---

### Коммит обновлённой программы

```bash
git commit -am "update hello world greeting"
git push origin main
```

Вывод в Linux:

```text
[main 100f693] update hello world greeting
 1 file changed, 5 insertions(+), 3 deletions(-)

Enumerating objects...
Counting objects: 100%
Writing objects: 100%
To https://github.com/ponomaryovmiron/lab02hw.git
```

---

### Создание ветки patch1

```bash
git checkout -b patch1
```

Вывод в Linux:

```text
Switched to a new branch 'patch1'
```

---

### Проверка программы в patch1

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Вывод в Linux:

```text
Hello world from @miron
```

---

### Коммит и push patch1

```bash
git add hello_world.cpp
git commit -m "remove using namespace std"
git push -u origin patch1
```

Вывод в Linux:

```text
[patch1 d2a9a63] remove using namespace std
 1 file changed, 3 insertions(+), 3 deletions(-)

Enumerating objects...
Counting objects: 100%
Writing objects: 100%
remote: Create a pull request for 'patch1' on GitHub
To https://github.com/ponomaryovmiron/lab02hw.git
 * [new branch]      patch1 -> patch1
branch 'patch1' set up to track 'origin/patch1'.
```

---

### Коммит с комментариями в patch1

```bash
git add hello_world.cpp
git commit -m "add comments to hello world"
git push origin patch1
```

Вывод в Linux:

```text
[patch1 d974374] add comments to hello world
 1 file changed, 2 insertions(+)

Enumerating objects...
Counting objects: 100%
Writing objects: 100%
To https://github.com/ponomaryovmiron/lab02hw.git
```

---

### Обновление main после merge patch1

```bash
git checkout main
git pull origin main
git branch -d patch1
```

Вывод в Linux:

```text
Switched to branch 'main'

From https://github.com/ponomaryovmiron/lab02hw
 * branch            main       -> FETCH_HEAD
Updating ...
Fast-forward

Deleted branch patch1
```

---

### Создание ветки patch2

```bash
git checkout -b patch2
```

Вывод в Linux:

```text
Switched to a new branch 'patch2'
```

---

### Форматирование clang-format

```bash
clang-format -i --style=Mozilla hello_world.cpp
```

Вывод в Linux:

```text
вывод отсутствует
```

---

### Проверка программы после форматирования

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Вывод в Linux:

```text
Hello world from @miron
```

---

### Коммит и push patch2

```bash
git add hello_world.cpp
git commit -m "format code with clang-format"
git push -u origin patch2
```

Вывод в Linux:

```text
[patch2 1971ca6] format code with clang-format
 1 file changed, несколько insertions и deletions

Enumerating objects...
Counting objects: 100%
Writing objects: 100%
remote: Create a pull request for 'patch2' on GitHub
To https://github.com/ponomaryovmiron/lab02hw.git
 * [new branch]      patch2 -> patch2
branch 'patch2' set up to track 'origin/patch2'.
```

---

### Изменение main

```bash
git checkout main
git add hello_world.cpp
git commit -m "change comments in master"
git push origin main
```

Вывод в Linux:

```text
Switched to branch 'main'

[main 6f2ea5f] change comments in master
 1 file changed, 2 insertions(+), 2 deletions(-)

Enumerating objects...
Counting objects: 100%
Writing objects: 100%
To https://github.com/ponomaryovmiron/lab02hw.git
```

---

### Rebase patch2 и появление конфликта

```bash
git checkout patch2
git pull --rebase origin main
```

Вывод в Linux:

```text
Switched to branch 'patch2'

From https://github.com/ponomaryovmiron/lab02hw
 * branch            main       -> FETCH_HEAD

Auto-merging hello_world.cpp
CONFLICT (content): Merge conflict in hello_world.cpp
error: could not apply 1971ca6... format code with clang-format
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
```

---

### Продолжение rebase после решения конфликта

```bash
git add hello_world.cpp
git rebase --continue
```

Вывод в Linux:

```text
Successfully rebased and updated refs/heads/patch2.
```

---

### Проверка после решения конфликта

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Вывод в Linux:

```text
Hello world from @miron
```

---

### Отправка patch2 после rebase

```bash
git push origin patch2 --force
```

Вывод в Linux:

```text
Enumerating objects...
Counting objects: 100%
Writing objects: 100%
To https://github.com/ponomaryovmiron/lab02hw.git
 + oldhash...newhash patch2 -> patch2
```

---

### Обновление main после merge patch2

```bash
git checkout main
git pull origin main
git branch -d patch2
```

Вывод в Linux:

```text
Switched to branch 'main'

From https://github.com/ponomaryovmiron/lab02hw
 * branch            main       -> FETCH_HEAD
Updating ...
Fast-forward

Deleted branch patch2
```

---

### Проверка истории

```bash
git log --oneline --graph --all
```

Вывод в Linux:

```text
*   dbb5f63 (HEAD -> main, origin/main) Merge pull request #2 from ponomaryovmiron/patch2
|\  
| * 1971ca6 (origin/patch2) format code with clang-format
|/  
* 6f2ea5f change comments in master
*   7887876 Merge pull request #1 from ponomaryovmiron/patch1
|\  
| * d974374 (origin/patch1) add comments to hello world
| * d2a9a63 remove using namespace std
|/  
* 100f693 update hello world greeting
* 94ee833 add hello world program
* 857a744 Update README.md
* 9f77a76 added sources
* 580bbb2 added README.md and gitignore
```

