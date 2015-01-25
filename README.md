[![HUGE, formerly "php-login" logo](_tutorial/huge-logo.png)](http://www.php-login.net)

# HUGE

Just a simple user authentication solution inside a simple framework skeleton that works out-of-the-box.
Uses future-proof official bcrypt password hashing/salting implementation of PHP 5.5+ and comes with some nice
additional features.

TODO fix these links after release

[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/panique/php-login/badges/quality-score.png?b=develop)](https://scrutinizer-ci.com/g/panique/php-login/?branch=develop)
[![Code Coverage](https://scrutinizer-ci.com/g/panique/php-login/badges/coverage.png?b=develop)](https://scrutinizer-ci.com/g/panique/php-login/?branch=develop)
[![Build Status](https://scrutinizer-ci.com/g/panique/php-login/badges/build.png?b=develop)](https://scrutinizer-ci.com/g/panique/php-login/build-status/develop)

TODO linked index / jump-lists!

### The History of HUGE

This script was formerly named "php-login" and by far the most popular version of the 4 simple PHP user auth
scripts of The PHP Login Project (a collection of simple login scripts, made to prevent people from using totally
outdated and insecure MD5 password hashing, which was still very popular in the PHP world back in 2012).

Why the name "HUGE" ? It's a nice combination to 
[TINY](https://github.com/panique/tiny), 
[MINI](https://github.com/panique/mini) and 
[MINI2](https://github.com/panique/tiny), my other projects :)

### Features
* built with the official PHP password hashing functions, fitting the most modern password hashing/salting web standards
* users can register, login, logout (with username, email, password)
* [planned: OAuth2 implementation for proper future-proof 3rd party auth]
* password-forget / reset
* remember-me (login via cookie)
* account verification via mail
* captcha
* failed-login-throttling
* user profiles
* account upgrade / downgrade
* supports local avatars and remote Gravatars
* supports native mail and SMTP sending (via PHPMailer and other tools)
* uses PDO for database access for sure, has nice DatabaseFactory (in case your project goes big) 
* uses URL rewriting ("beautiful URLs")
* proper split of application and public files (requests only go into /public)
* uses Composer to load external dependencies (PHPMailer, Captcha-Generator, etc.)
* fits PSR-0/1/2/4 coding guidelines
* masses of comments
* is actively developed, maintained and bug-fixed

### Live-Demo

TODO
See a [live demonstration](http://php-login.net/demo4.html) or [see the server's phpinfo()](http://phpinfo.php-login.net/).

### Support the project

There a lot of work behind this project. I might save you hundreds, maybe thousands of hours of work (calculate that
in developer costs). So when you are earning money by using HUGE, be fair and give something back to open-source.
HUGE is totally free to private and commercial use.

TODO new banners

[![Donate with PayPal banner](_tutorial/donate-with-paypal.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=P5YLUK4MW3LDG)
[![Donate by server affiliate sale](_tutorial/support-a2hosting.png)](https://affiliates.a2hosting.com/idevaffiliate.php?id=4471&url=579)

You can also rent your next server at [DigitalOcean](https://www.digitalocean.com/?refcode=40d978532a20) or donate via 
[PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=P5YLUK4MW3LDG).
Feel free to contribute to this project.

### Follow the project

Here on **[Twitter](https://twitter.com/simplephplogin)** or  
**[Facebook](https://www.facebook.com/pages/PHP-Login-Script/461306677235868)**. 
I'm also blogging on **[Dev Metal](http://www.dev-metal.com)**.

### License

Licensed under [MIT](http://www.opensource.org/licenses/mit-license.php). Totally free for private or commercial projects.

### Requirements

Make sure you know the basics of object-oriented programming and MVC, are able to use the command line and have
used Composer before. This script is not for beginners.

* **PHP 5.5+**
* **MySQL 5** database (better use versions 5.5+ as very old versions have a [PDO injection bug](http://stackoverflow.com/q/134099/1114320)
* installed PHP extensions: pdo, gd, openssl (the install guideline shows how to do)
* installed tools on your server: git, curl, composer (the install guideline shows how to do)
* for professional mail sending: an SMTP account (I use [SMTP2GO](http://www.smtp2go.com/?s=devmetal))
* activated mod_rewrite on your server (the install guideline shows how to do)

### Installation

TODO

* Change the VirtualHost file from DocumentRoot /var/www/html to DocumentRoot /var/www/html/public and from 
<Directory "/var/www/html"> to <Directory "/var/www/html/public">. Don't forget to restart.
http://www.dev-metal.com/enable-mod_rewrite-ubuntu-14-04-lts/

### Testing with demo user

By default HUGE has a demo-user: username is `demo`, password is `12345678`. The user is already activated.

### Contribute

Please commit only in *develop* branch. The *master* branch will always contain the stable version.

### Found a bug (Responsible Disclosure) ?

Due to the possible consequences when publishing a bug on a public open-source project I'd kindly ask you to send really
big bugs to my email address, not posting this here. If the bug is not interesting for attackers: Feel free to create
an normal GitHub issue.

## Current and further development

See active issues and requested features here:
https://github.com/panique/php-login/issues?state=open








## Installation on Ubuntu 12.04 LTS

This installation guideline uses Ubuntu 12.04 LTS (as it is the standard and by far the most long-term supported
mainstream server OS (supported until 2017). For more, see the
[Wikipedia page of Ubuntu versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions).

When developing in a Vagrant box: please note that it's quite difficult to identify a Vagrant box to Facebook's App API,
so currently there's no guideline on how to use the Facebook login-feature when using a LOCAL Vagrant box.
For more, see [this StackOverflow question](http://stackoverflow.com/questions/20615924/how-to-run-a-facebook-app-on-an-ip-domain-works-localhost-works-ip-does-not).

#### ON YOUR SERVER (we use Ubuntu 12.04 LTS here):
1. install Apache, MySQL, PHP and eventually PHPMyAdmin: [How to setup a LAMP stack on Ubuntu 12.04](http://www.dev-metal.com/setup-basic-lamp-stack-linux-apache-mysql-php-ubuntu-12-04/)
2. install mod_rewrite and activate it: [How to enable mod_rewrite in Ubuntu 12.04 LTS](http://www.dev-metal.com/enable-mod_rewrite-ubuntu-12-04-lts/)
3. install Composer: [How to install Composer on Ubuntu](http://www.dev-metal.com/install-update-composer-windows-7-ubuntu-debian-centos/)
4. install GD (for the Captcha): `sudo apt-get install php5-gd`, restart Apache `sudo service apache2 restart`
5. install OpenSSL (to send mails): `sudo apt-get install openssl`, restart Apache `sudo service apache2 restart`
6. remove all files from the */var/www* (should only be Apache's index.html and your phpinfo()-containing .php right now) with `rm -r /var/www/*`,
otherwise things will get messy and git won't download the repo into a non-empty folder
7. copy the contents of the extracted php-login repository into /var/www ! In this tutorial we don't use a sub-folder,  so your index.php should go into /var/www !
Best way to do is cloning via git: `git clone https://github.com/panique/php-login.git /var/www` or by creating the
project via Composer: `composer create-project panique/php-login /var/www dev-master`
8. Make the repo's folder *public/avatars* writable via `chmod 775 /var/www/public/avatars` and check its rights with `stat /var/www/public/avatars`
9. Run the three SQL statements in the *application/_installation/sql_statements* folder (the installation folder has an underscore in front of its name, but GitHub doesn't show this due to
a bug in its README-parser), via PHPMyAdmin (look at the files directly on https://github.com/panique/php-login/) or do it via mysql command-line

#### CONFIGS IN THE CODE:

In *application/config/config.php*:

11. enter your database credentials in DB_USER, DB_PASS etc.
12. enter your project URL into URL, don't forget the trailing slash!
13. edit COOKIE_DOMAIN to the above URL
14. in the SMTP block, set EMAIL_USE_SMTP tp `true` and put in your SMTP provider credentials ((I use [SMTP2GO](http://www.smtp2go.com/?s=devmetal))). Please remember:
You cannot simply send emails with PHP's mail() function, this does not really work due to a lot of reasons.
For development it could make sense to set PHPMAILER_DEBUG_MODE to 2 as this will echo out errors and notices when sending mails.
15. OPTIONAL for development (better leave it like it is !), but necessary for production environments: Change the text,
reply-mail-address etc. of the EMAIL_PASSWORD_RESET_SUBJECT etc.

In *.htaccess*:

1. Change the RewriteBase: when using the script within a sub-folder, put this path here, like */mysubfolder/* !
If your app is in the root of your web folder, then delete this line or comment it out.

#### RUN COMPOSER:
1. go into the base folder of your application (where composer.json is) (`cd /var/www`) and do `composer install` on the command line

**Voila!** You app should now run fine.

#### To use the (optional) Facebook login

Note: Facebook changes the look, the UI and the way the Facebook App pages work permanently. But you'll find out what's
meant. Go to https://developers.facebook.com/apps/ and create a new app.
Go to "preferences" or whatever it is called, enter your email adress, leave "App Domain" empty, click on "Add platform"
and put your URL in "Site URL" (completely with "http://www."), save. For local development "localhost" works.
Things like "127.0.0.1" don't seem work. In earlier version of Facebook's App API you needed to set "sandbox mode" to
"deactivated", now... well... I don't know, they have removed the button but the app still says "in development mode".

Set `FACEBOOK_LOGIN` in *application/config/config.php* to `true` and put your Facebook app id and the secret token
in `FACEBOOK_LOGIN_APP_ID` and `FACEBOOK_LOGIN_APP_SECRET`.

You should see the Facebook login / register buttons on the login / register page of your php-login app now.

## Useful links

- [How to use PDO](http://wiki.hashphp.org/PDO_Tutorial_for_MySQL_Developers)
- [A short guideline on how to use the PHP 5.5 password hashing functions and its PHP 5.3 & 5.4 implementations](http://www.dev-metal.com/use-php-5-5-password-hashing-functions/)
- [How to setup latest version of PHP 5.5 on Ubuntu 12.04 LTS](http://www.dev-metal.com/how-to-setup-latest-version-of-php-5-5-on-ubuntu-12-04-lts/)
- [How to setup latest version of PHP 5.5 on Debian Wheezy 7.0/7.1 (and how to fix the GPG key error)](http://www.dev-metal.com/setup-latest-version-php-5-5-debian-wheezy-7-07-1-fix-gpg-key-error/)
- [Notes on password & hashing salting in upcoming PHP versions (PHP 5.5.x & 5.6 etc.)](https://github.com/panique/php-login/wiki/Notes-on-password-&-hashing-salting-in-upcoming-PHP-versions-%28PHP-5.5.x-&-5.6-etc.%29)
- [Some basic "benchmarks" of all PHP hash/salt algorithms](https://github.com/panique/php-login/wiki/Which-hashing-&-salting-algorithm-should-be-used-%3F)
- [How to prevent PHP sessions being shared between different apache vhosts / different applications](http://www.dev-metal.com/prevent-php-sessions-shared-different-apache-vhosts-different-applications/)

You can find more in the project's [github wiki](https://github.com/panique/php-login/wiki).

#### If you like the folder/file structure

Then have a look into the partner project PHP-MVC on http://www.php-mvc.net and https://github.com/panique/php-mvc.
A super-reduced and naked bare-bone application.

## How the facebook login process works

https://github.com/facebook/facebook-php-sdk

https://developers.facebook.com/docs/php/gettingstarted/

## Used packages (via composer)

PHPMailer
https://packagist.org/packages/phpmailer/phpmailer

PHP password compatibility library
https://packagist.org/packages/ircmaxell/password-compat

Facebook SDK
https://packagist.org/packages/facebook/php-sdk

Gregwar's Captcha
https://packagist.org/packages/gregwar/captcha

Kint (a better var_dump)
https://packagist.org/packages/raveren/kint

## Thanks

This project is kindly powered by **[PHPStorm](http://www.jetbrains.com/phpstorm/)**.
A big "Thank You!" to IntelliJ for giving php-login free licenses of this wonderful IDE.

## Hire me

I'm available for freelance work, mainly PHP and frontend. Remote worldwide or locally around Central Europe.
Please send a mail if you like, you can find out my email address easily.
