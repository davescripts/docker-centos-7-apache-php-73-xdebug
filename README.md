# Docker Container: Centos7, Apache, PHP 7.3, and Xdebug

Set up Xdebug on a Docker Container with Centos 7, and PHP 7.3.

More details can be found [here](https://davescripts.com/setup-xdebug-on-docker-container-with-centos7-php-73).

<br>

## Build

Create Docker Image.

```sh
docker build -t <image_name> .
```

_Replace **&lt;image_name&gt;** with the name you want for the image._

<br>

Example.

```sh
docker build -t image_apache .
```

<br>

## Run

Create Docker Container.

```sh
docker run -tid -p 4000:80 --name=<container_name> -v /path_to/folder:/var/www/html <image_name>
```

_Replace **&lt;container_name&gt;** with the name you want for the container, and **&lt;image_name&gt;** with the name of the image you specified on the Build command above._

<br>

Example.

```sh
docker run -tid -p 4000:80 --name=container_apache -v /path_to/folder:/var/www/html image_apache
```

_Also change **"/path_to/folder"** with the actual location of your website's root folder on your local machine._

<br>

## Check Xdebug Installation

To check Xdebug has been correctly installed and configured, open a terminal window into the Docker Container with the following command:

```sh
docker exec -it container_apache bash
```

<br>

Then, on the terminal window inside the container, we will use the php -i instruction to get information about our PHP installation. We will also use the grep utility to display only the information relevant to Xdebug:

```sh
php -i | grep xdebug
```
<br>

You will see an output similar to this one (excerpts):

> xdebug<br/>
xdebug support => enabled<br/>
Support Xdebug on Patreon, GitHub, or as a business: https://xdebug.org/support<br/>
xdebug.auto_trace => Off => Off<br/>
xdebug.cli_color => 0 => 0<br/>
...<br/>
xdebug.remote_autostart => On => On<br/>
xdebug.remote_connect_back => Off => Off<br/>
xdebug.remote_cookie_expire_time => 3600 => 3600<br/>
xdebug.remote_enable => On => On<br/>
xdebug.remote_host => host.docker.internal => host.docker.internal<br/>
xdebug.remote_log => no value => no value<br/>
...<br/>
