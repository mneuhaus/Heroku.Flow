Heroku.Flow
===========

TYPO3 Flow is a CodeIgniter boilerplate to get you running in minutes. Include CodeIgniter 2.1.3, HTML5 BoilerPlate, Twitter Bootstrap & more. AppStrap is easy to get running on Heroku in under a minute with a few simple commands

	$ git init flowapp
	$ cd flowapp
	$ git pull git@github.com:svparijs/Heroku.Flow.git
	$ heroku apps:create -b git://github.com/svparijs/heroku-buildpack-php-flow.git
	$ git push heroku master

Configuration
-------------

The config files are bundled:

conf/nginx.conf.erb
conf/etc.d/01_memcached.ini
conf/etc.d/02_memcache.ini
conf/etc.d/03_phpredis.ini
conf/php.ini
conf/php-fpm.conf

Overriding Configuration Files During Deployment
------------------------------------------------

Create a conf/ directory in the root of the your deployment. Any files with names matching the above will be copied over and overwitten.

This way, you can customise settings specific to your application, especially the document root in nginx.conf.erb. (Note the .erb extension.)

Custom buildpack
----------------

The key thing you need to do, is change BUILDPACK_URL to your own fork of the [heroku-buildpack-php](https://github.com/heroku/heroku-buildpack-php)

	$ heroku config:set BUILDPACK_URL=git://github.com/svparijs/heroku-buildpack-php-flow.git


Deploying
---------

To use this buildpack, on a new Heroku app:

	$ heroku create -s cedar -b git://github.com/svparijs/heroku-buildpack-php-flow.git
	$ heroku config:add PATH="/app/vendor/bin:/app/local/bin:/app/vendor/nginx/sbin:/app/vendor/php/bin:/app/vendor/php/sbin:/usr/local/bin:/usr/bin:/bin"

On an existing app:

	$ heroku config:add BUILDPACK_URL=git://github.com/svparijs/heroku-buildpack-php-flow.git
	$ heroku config:add PATH="/app/vendor/bin:/app/local/bin:/app/vendor/nginx/sbin:/app/vendor/php/bin:/app/vendor/php/sbin:/usr/local/bin:/usr/bin:/bin"

Feedback
--------

Please contact me via twitter [@van2parijs](https://twitter.com/van2parijs)

Resources
---------

- [Blog post of original package](http://blog.iphoting.com/blog/2012/05/24/running-php-on-heroku/)

- [Hacking a buildpack](https://blog.heroku.com/archives/2012/11/13/hacking-buildpacks/)

Credits
-------

Original buildpack adapted and modified for Nginx + PHP support by Ronald Ip.

Buildpack originally inspired, and forked from [https://github.com/heroku/heroku-buildpack-php](https://github.com/heroku/heroku-buildpack-php).