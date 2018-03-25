# 10. Webpack, сборка, запуск dev ноды
* В папке с конфигом webpack создать папку web.
* Установить пакеты
```bash
yarn cache clean && yarn upgrade
``` 
* Пример файла package.json
```json
{
  "name": "webpack",
  "version": "1.0.0",
  "license": "MIT",
  "scripts": {
    "dev": "cross-env NODE_ENV=development USER=${USER} webpack-dev-server --socket /tmp/prod.sock --progress --no-inline",
    "dev-windows": "cross-env NODE_ENV=development USER=${USER} webpack-dev-server --host=127.0.0.1 --port=9229 --progress --no-inline",
    "build": "cross-env NODE_ENV=production webpack --progress --hide-modules"
  },
  "dependencies": {
    "bootstrap": "3.3",
    "jquery": "^3.2.1",
    "lodash": "^4.17.4",
    "magnific-popup": "^1.1.0",
    "stompjs": "^2.3.3"
  },
  "devDependencies": {
    "autoprefixer": "^6.7",
    "babel-core": "^6.25",
    "babel-loader": "^7.1",
    "babel-plugin-array-includes": "^2.0.3",
    "babel-plugin-transform-object-assign": "^6.22.0",
    "babel-plugin-transform-object-rest-spread": "^6.23",
    "babel-polyfill": "^6.23",
    "babel-preset-env": "^1.6.0",
    "babel-preset-latest": "^6.24",
    "copy-webpack-plugin": "^4.0",
    "cross-env": "3.2.4",
    "css-loader": "^0.28.7",
    "extract-text-webpack-plugin": "3.0.0",
    "file-loader": "^1.0",
    "html-webpack-plugin": "^2.29",
    "node-sass": "^4.5.3",
    "sass-loader": "^6.0.6",
    "style-loader": "^0.19.1",
    "url-loader": "^0.6.2",
    "webpack": "^3.6",
    "webpack-dev-server": "^2.8"
  }
}
``` 
*  Для сборки проекта необходимо в директории webpack запустить команду:
```bash
npm run build
```
* Для сборки в режиме разработки необходимо внести изменения в конфигурационный файл nginx или другого сервера, чтобы отдача файлов происходила через порт или сокет (ниже пример конфига для nginx на openserver-e, прошу обратить внимание что адрес сервера представлен стандартной переменной %ip%). Для windows лучше запускать через порт, для этого необходимо в директории webpack запустить команду (в результате выполнения команды будет запущена нода и соответствующий процесс, который будет висеть пока dev окружение необходимо):
```bash
npm run dev-windows
```
 ```apacheconfig
location ~* \.(js|css)$ {
    proxy_intercept_errors on; 
    recursive_error_pages on;
    error_page 400 401 402 403 404 = @assets;
    error_page 500 501 502 503 504 = @assets;

    proxy_pass http://%ip%:9229;
}
 location @assets {
    try_files $uri =404;
}
```
 