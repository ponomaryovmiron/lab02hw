# Отчёт по домашнему заданию ЛР №2


## Клонирование tutorial-репозитория

```bash
cd "/home/vboxuser/Рабочий стол/project/projects/ponomaryovmiron_labs"
```

Переход в папку с лабораторными работами аккаунта `ponomaryovmiron`.

```bash
rm -rf lab02hw
```

Удаление старой папки `lab02hw`, если она уже была.

```bash
git clone https://github.com/ponomaryovmiron/lab02tut.git lab02hw
```

Клонирование tutorial-репозитория `lab02tut` в новую папку `lab02hw`.

```bash
cd lab02hw
```

Переход в папку домашнего задания.

```bash
git remote remove origin
```

Удаление старой ссылки на репозиторий `lab02tut`.

```bash
git remote add origin https://github.com/ponomaryovmiron/lab02hw.git
```

Добавление новой ссылки на репозиторий `lab02hw`.

```bash
git branch -M main
```

Переименование основной ветки в `main`.

```bash
git config --global user.name "ponomaryovmiron"
git config --global user.email "godgezuru@gmail.com"
```

Настройка имени пользователя и почты для коммитов.

## Создание программы hello_world

```bash
cat > hello_world.cpp
```

Был создан файл `hello_world.cpp`.

В первой версии программа просто выводила сообщение:

```cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world" << endl;
    return 0;
}
```

```bash
g++ hello_world.cpp -o hello_world
```

Компиляция программы.

```bash
./hello_world
```

Запуск программы.

```bash
rm -f hello_world
```

Удаление исполняемого файла, чтобы он не попал в репозиторий.

```bash
git add hello_world.cpp
git commit -m "add hello world program"
git push origin main
```

Добавление файла в Git, создание коммита и отправка изменений в GitHub.

## Изменение программы

Далее программа была изменена: теперь она считывает имя пользователя и выводит сообщение в формате:

```text
Hello world from @name
```

Файл `hello_world.cpp` был изменён:

```cpp
#include <iostream>
#include <string>
using namespace std;

int main()
{
    string name;
    cin >> name;

    cout << "Hello world from @" << name << endl;

    return 0;
}
```

Проверка работы:

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Команды компилируют программу, запускают её с тестовым вводом `miron` и удаляют исполняемый файл.

```bash
git commit -am "update hello world greeting"
git push origin main
```

Фиксация изменений и отправка их в основную ветку.

## Ветка patch1

```bash
git checkout -b patch1
```

Создание новой ветки `patch1`.

В этой ветке из программы был убран `using namespace std`.
Код стал аккуратнее, потому что теперь используются полные имена из пространства `std`.

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string name;
    std::cin >> name;

    std::cout << "Hello world from @" << name << std::endl;

    return 0;
}
```

Проверка:

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Коммит и отправка ветки:

```bash
git add hello_world.cpp
git commit -m "remove using namespace std"
git push -u origin patch1
```

После этого на GitHub был создан Pull Request из ветки `patch1` в `main`.

## Добавление комментариев в patch1

В ветке `patch1` были добавлены комментарии:

```cpp
// Read user name from standard input.
std::string name;
std::cin >> name;

// Print greeting message.
std::cout << "Hello world from @" << name << std::endl;
```

Команды:

```bash
git add hello_world.cpp
git commit -m "add comments to hello world"
git push origin patch1
```

После отправки изменений Pull Request обновился. Затем он был слит в ветку `main`.

После merge были выполнены команды:

```bash
git checkout main
git pull origin main
git branch -d patch1
```

Команды переключают проект на ветку `main`, забирают актуальные изменения с GitHub и удаляют локальную ветку `patch1`.

## Ветка patch2

```bash
git checkout -b patch2
```

Создание новой ветки `patch2`.

В этой ветке код был отформатирован с помощью `clang-format` в стиле Mozilla:

```bash
clang-format -i --style=Mozilla hello_world.cpp
```

После форматирования программа была проверена:

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

Затем изменения были закоммичены и отправлены:

```bash
git add hello_world.cpp
git commit -m "format code with clang-format"
git push -u origin patch2
```

После этого был создан Pull Request из `patch2` в `main`.

## Изменение main и появление конфликта

В ветке `main` были изменены комментарии в файле `hello_world.cpp`:

```cpp
// Input user name.
std::string name;
std::cin >> name;

// Output message to console.
std::cout << "Hello world from @" << name << std::endl;
```

Команды:

```bash
git checkout main
git add hello_world.cpp
git commit -m "change comments in master"
git push origin main
```

Из-за этого при обновлении ветки `patch2` появился конфликт.

## Решение конфликта

Ветка `patch2` была обновлена через rebase:

```bash
git checkout patch2
git pull --rebase origin main
```

Git сообщил о конфликте в файле `hello_world.cpp`.

Файл был исправлен вручную. Итоговый вариант:

```cpp
#include <iostream>
#include <string>

int
main()
{
  // Input user name.
  std::string name;
  std::cin >> name;

  // Output message to console.
  std::cout << "Hello world from @" << name << std::endl;

  return 0;
}
```

После исправления конфликта были выполнены команды:

```bash
git add hello_world.cpp
git rebase --continue
```

Команды добавляют исправленный файл и продолжают rebase.

Проверка программы:

```bash
g++ hello_world.cpp -o hello_world
echo "miron" | ./hello_world
rm -f hello_world
```

После успешной проверки ветка `patch2` была отправлена на GitHub:

```bash
git push origin patch2 --force
```

`--force` использовался потому, что после rebase история ветки изменилась.

## Слияние patch2

После исправления конфликта Pull Request `patch2` был слит в ветку `main`.

После merge были выполнены команды:

```bash
git checkout main
git pull origin main
git branch -d patch2
```

Команды переключают проект на основную ветку, загружают последние изменения и удаляют локальную ветку `patch2`.

## Проверка истории

```bash
git log --oneline --graph --all
```

Команда показывает историю коммитов в виде графа.

В истории видно, что были выполнены два Pull Request:

```text
Merge pull request #1 from ponomaryovmiron/patch1
Merge pull request #2 from ponomaryovmiron/patch2
```

История:
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
