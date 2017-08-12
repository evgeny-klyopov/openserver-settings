# 6. Добавление nano в консоль gitBash
### Запуск nano ломает встроенный в gitBash редактор vim, также при установленном параметре chcp 65001 ломается кодировка уже в самом редакторе nano. В связи с этим использовать данный редактор не рекомендуется. 

Переходим в директорию git
```
cd modules/git/
```
создаём папку share
```
mkdir share
```
переходим в папку share
```
cd share/
```
скачиваем пакет nano
```
curl -L -O http://www.nano-editor.org/dist/v2.2/NT/nano-2.2.6.zip
```
распаковываем его
```
unzip  nano-2.2.6.zip -d nano
```
удаляем архив
```
rm nano-2.2.6.zip
```
**копируем** файл nano в директорию modules/git/bin

![Установка nano](img/install-nano.png "Установка nano")