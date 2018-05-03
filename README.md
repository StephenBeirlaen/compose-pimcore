Pimcore compose environment
===========================

Dockerwest Compose Environment for [Pimcore](https://www.pimcore.org/).

For detailed documentation, [visit our website](https://dockerwest.github.io/compose-pimcore/)


***When using Pimcore 5, please use the "pimcore5" branch!***


Usage
-----

For your convenience the developer environment has some helpers which take away
some difficulties you could experience using docker containers.

If you want this easy helpers to be readily available for you you can use
`environment` before you start. `environment` allows you to start your
environment with an updated `PATH` and allows you to choose between `tmux`,
`screen` or `byobu`. You can also define a default in the .env file. 

explicit setting the window manager:

~~~ sh
$ ./environment [tmux|screen|byobu]
~~~

using default window manager, defined in .env

~~~ sh
$ ./environment
~~~

When you are running in this environment all helpers are available in your path.

You are not required to use the environent, but then you have to call the
helpers with their full path.

To make use of the helpers you should use the `run` wrapper for `docker-compose`.

~~~ sh
$ run up
~~~

Configuration
-------------

There is a sample configuration `.env-sample` which contains the defaults used
in this environment.

If you want to change some of these values, copy `.env-sample` to `.env` and
start editing.

default `.env-sample`

~~~
C_UID=1000
C_GID=1000
PHPVERSION=7.1
NGINXVERSION=stable
BASEHOST=pimcore.docker
MYSQL_ROOT_PASSWORD=toor
APPLICATION=../pimcore
DEVELOPMENT=noprofile
WINDOW_MANAGER=tmux
~~~

##### C_UID / C_GID

Configure what UID and GID your PHP container must use. This usually should
match your Hosts UID and GID. To find your local UID you can run `id -u` and to
find your local GID you can run `id -g`.

##### PHPVERSION

Choose your PHP version. To see which versions are available
[here](https://github.com/dockerwest/php-pimcore).

##### NGINXVERSION

Choose what version of Nginx you want. To see which versions are available see
[here](https://github.com/dockerwest/nginx-pimcore)

##### BASEHOST

This setting defines what the hostname will be you can browse your pimcore app.
The example configuration will be give you `http://pimcore.docker`.

##### MYSQL_ROOT_PASSWORD

Choose whatever you want to use as default root password.

##### APPLICATION

A relative or absolute path to your pimcore code. this can be a checkout of
  [pimcore](https://github.com/pimcore/pimcore).

##### DEVELOPMENT

Set the development flag. Default we use noprofile which will allow us to use
xdebug. When `DEVELOPMENT=1` you also have tideways enabled which gives you
profiling output of you application.

To visualize your profiling output see
[docker-compose-xhgui](https://github.com/BlackIkeEagle/docker-compose-xhgui)

##### WINDOW_MANAGER
Set the default window manager when running the environment.
Available options are: tmux, screen and byobu

Helpers
-------

The helpers are written in python, so you should have python2 or python3
installed on your system to be able to use them. Most Linux distributions and
macOS have python already installed so there should be no issue there. There
are no extra dependencies on python modules.

For detailed information on helpers, see [our website](https://dockerwest.github.io/compose-pimcore/)

License
-------

MIT License (MIT). See [License File](LICENSE.md) for more information.
