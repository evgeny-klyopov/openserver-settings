# 13. Deployer client
* Установка пакета для deploy
```bash
curl -LO https://deployer.org/deployer.phar
mv deployer.phar /usr/bin/dep
chmod +x /usr/bin/dep
```
* Добавляем публичный ключ авторизации на сервер в авторизованные ключи
```bash
cat ~/.ssh/id_rsa.pub
```
* Чтобы deploy заработал на Windows необходимо выключить tty и multiplexing в файле конфигурации deploy.php
```php
set('ssh_multiplexing', false);
set('git_tty', false);
```
* Deploy
```bash
dep deploy stageName
```







