# 1. Настройка консоли (интеграция gitbash в консоль OpenServer-а)
* **Скопировать** файл git-bash.bat в корень модуля git (\modules\git)
* Открыть консоль => Setup tasks... => и добавить новую со следующими параметрами запуска - 
    ```
    "%ConEmuDir%\..\git\git-bash.bat" --no-cd --command=usr/bin/bash.exe -l -i
    ```

    ![Открыть консоль](img/console.png "Открыть консоль")

    В настройках старта(Startup) можно выбрать консоль по умолчанию
