Prerequisites:
PHP > 7.0
Web server (Apache/Ngnix)
Node and npm

Please follow below steps to install the package to a new Laravel or an existing Laravel site:

1) Install package using "composer install xparthxvorax/larachat" command

2) Run "php artisan larachat:install" command

3) Setup front-end:
- Run "npm install -g laravel-echo-server" command
- Add below dependencies to the package.json file:
"dependencies": {
   "laravel-echo": "^1.4.1",
   "socket.io-client": "^2.1.1"
}
- Run "npm install" command
- Add below lines to "resources/js/bootstrap.js"
import Echo from "laravel-echo"
window.io = require('socket.io-client');
window.Echo = new Echo({
    broadcaster: 'socket.io',
    host: window.location.hostname + ':6001'
});
- Add below lines to "resources/js/app.js"
Vue.component('larachat-component', require('./components/LaraChatComponent.vue'));
- Add <larachat-component></larachat-component> in resources/views/home.blade.php (or wherever you want to display user list)

4) Set BROADCAST_DRIVER=redis and add LARAVEL_ECHO_SERVER_AUTH_HOST=your-site-url

5) npm run dev

6) Run "laravel-echo-server start" to start socket server. Keep the command running or you may use supervisor for that(https://laravel.com/docs/master/queues#supervisor-configuration)