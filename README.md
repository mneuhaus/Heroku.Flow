Heroku.Flow
===========

TYPO3 Flow is a CodeIgniter boilerplate to get you running in minutes. Include CodeIgniter 2.1.3, HTML5 BoilerPlate, Twitter Bootstrap & more. AppStrap is easy to get running on Heroku in under a minute with a few simple commands

	$ git init flowapp
	$ cd flowapp
	$ git pull git@github.com:svparijs/Heroku.Flow.git
	$ heroku apps:create -b git://github.com/svparijs/heroku-buildpack-php#appstrap
	$ git push heroku master

Custom buildpack
----------------

The key thing you need to do is change BUILDPACK_URL to your own fork of the [heroku-buildpack-php](https://github.com/heroku/heroku-buildpack-php)

	$ heroku config:set BUILDPACK_URL=git://github.com/winglian/heroku-buildpack-php.git#mpm-event-php-fpm


Deploying

To use this buildpack, on a new Heroku app:

heroku create -s cedar -b git://github.com/iphoting/heroku-buildpack-php-tyler.git
On an existing app:

heroku config:add BUILDPACK_URL=git://github.com/iphoting/heroku-buildpack-php-tyler.git
heroku config:add PATH="/app/vendor/bin:/app/local/bin:/app/vendor/nginx/sbin:/app/vendor/php/bin:/app/vendor/php/sbin:/usr/local/bin:/usr/bin:/bin"