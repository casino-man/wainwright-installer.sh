# wainwright-installer.sh
installer without docker for ubuntu &amp; debian -- for fast dev setup with wainwright casino plugins: https://gitlab.com/casinoman

## steps (important):
- make sure to enter the domain as "APP_URL" in .env.casinodog before you do anything, as it's used for nginx setup etc.
- you can enter latest wainwright git repositories within .env.casinodog
- place cert.crt & private.key for your domain within the root working folder
- execute `sudo chmod a+x`, followed by ./installer.sh

## after install
- `cd casinodog`
- check if the `.wainwright` folder is populated with plugin folders: `ls .wainwright`
- check if composer copied properly and is including the 'wainwright/*' packages
- if all is fine, execute `composer update --no-cache --no-ansi --ignore-platform-reqs`
- restart webserver & php: `service nginx restart && service php8.1-fpm restart`
- finish off with `chown -R www-data:www-data .`

**do not touch nginx_boilerplate.conf && composer_template.json - it will copy and symbolic link in working directory a new nginx config file with name of your domain: ${APP_URL}.conf**

Installer will get fresh laravel setup from github. It's pretty rough and *sturdy* installer.sh meant for spin-up vpses to just get into development faster.
