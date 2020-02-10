# Installation

## On a dedicated web server (recommended way)

To install wallabag itself, you must run the following commands:

```bash
git clone https://github.com/wallabag/wallabag.git
cd wallabag && make install
```

If it's your first installation, you can safely answer "yes" when asking to reset the database.

Now, read the next step to create your virtual host, then
access your wallabag.

{% hint style="info" %}
To define parameters with environment variables, you have to set these variables with `SYMFONY__` prefix, for example, `SYMFONY__DATABASE_DRIVER`.
You can have a look at [Symfony documentation](http://symfony.com/doc/current/cookbook/configuration/external_parameters.html).
{% endhint %}

{% hint style="tip" %}
If you want to use SQLite to store your data, please put `%kernel.root_dir%/../data/db/wallabag.sqlite` for the `database_path` parameter during installation.
{% endhint %}

{% hint style="info" %}
If you're installing Wallabag behind Squid as a reverse proxy, make sure to update your `squid.conf` configuration to include `login=PASS` in the `cache_peer` line. This is necessary for API calls to work properly.
{% endhint %}

## On shared hosting

We provide a package with all dependencies inside. The default
configuration uses MySQL for the database. If you want to change these
settings, please edit `app/config/parameters.yml`.

With this package, wallabag doesn't check for mandatory extensions used
in the application (theses checks are made during `composer install`
when you have a dedicated web server, see above).

Execute this command to download and extract the latest package (please replace the version with the latest one) :

```bash
wget https://static.wallabag.org/releases/wallabag-release-2.3.8.tar.gz && tar xvf latest-v2-package
```

You will find the [md5 hash of the latest package on our
website](https://wallabag.org/en#download).

Now, read the next step to create your virtual host, then
access your wallabag.

To create a new user, please use the register form. Then, in order to have admin
permissions, please run this query in your favorite DMBS (by replacing `1` with
the id for this new user):

```sql
UPDATE wallabag_user SET roles = 'a:2:{i:0;s:9:"ROLE_USER";i:1;s:16:"ROLE_SUPER_ADMIN";}' where id = 1;
```

## Usage of wallabag.it

[wallabag.it](https://wallabag.it) is a paid service to use wallabag without installing it on a web server.

This service always ships the latest release of wallabag. [You can create your account here](https://app.wallabag.it/). Try it for free: you'll get a 14-day free trial with no limitation (no credit card information required).

## Installation with Docker

We provide you a Docker image to install wallabag easily. Have a look at
our repository on [Docker
Hub](https://hub.docker.com/r/wallabag/wallabag/) for more information.

### Command to launch container

```bash
docker pull wallabag/wallabag
```

## Installation on Cloudron

Cloudron provides an easy way to install webapps on your server with a
focus on sysadmin automation and keeping apps updated. wallabag is
packaged as a Cloudron app and available to install directly from the
store.

[Install wallabag on your
Cloudron](https://cloudron.io/store/org.wallabag.cloudronapp.html)

## Installation on YunoHost

YunoHost provides an easy way to install webapps on your server with a
focus on sysadmin automation and keeping apps updated. wallabag is
packaged as an official YunoHost app and is available to install directly from the
official repository.

[![Install wallabag with
YunoHost](https://install-app.yunohost.org/install-with-yunohost.png)](https://install-app.yunohost.org/?app=wallabag2)

## Installation on Synology

The SynoCommunity provides a package to install wallabag on your Synology NAS.

[Install wallabag with Synology](https://synocommunity.com/package/wallabag)
