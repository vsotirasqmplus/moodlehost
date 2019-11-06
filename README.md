# MoodleHost

## What is this?
MoodleHost is based on the Docker image mooldehq/moolde-php-apache and adds xdebug with sessionkey PHPSTORM. 
It provides a Apache web server with all the trimmings ready to run a Moodle environment for development or testing.

<b style="color: #ff0000;">ATTENTION:</b> The resulting web server is by no means secure. Never use it for production environments!


## Preliminaries
You need to have Docker installed to use MoodleHost.

## Installation
To install MoodleHost on you need to run the install_moodlehost script as superuser (e.g. <i>$ sudo ./install_moodlehost</i>). Duriung the installation you will be promted to edit the moodlehost configuration file (/etc/moodlehost.conf). The configiuration file allows to set default values for the installation like the port and PHP version used. Values in moodlehost.conf may be overridden by options when running the moodlehost command

## moodlehost.conf
The configuration file will be installed into /etc/moodlehost.conf and contains the default values when running moodlehost without options.

## the moodlehost command
There are several options available when running moodlehost from a command line:

	-d <database-server-ip-address>: This will determine the IP address of the mysql database server. Inside moodlehost this address is then mapped to 'db_host'.

	-f <path/to/filedir>: Mapping an existing filedir repository on the host into /var/www/moodledata/filedir.

	-m <path-to-moodledata>: By default moodlehost will create/use a folder 'moodledata' within the hosted directory. With this option a different location may be used.

	-p <port>: The port the Apache web server will be using. (default = 80)

	-v <php-version>: Set the PHP version that will be used. Valid values are: 5.6, 7.0, 7.1, 7.2, 7.3 (default = 7.3)

	-w <path/to/webroot>: Set path to the webroot directory (default = $PWD)

## Usage
To use moodlehost simply change into the directory you want to host. There you may issue '<i>$ moodlehost start</i>' to start a server with default values (as of /etc/moodlehost.conf).

Now point your browser to "http://localhost[:port]" to see the resulting web page.

<b>Please note:</b> the resulting Docker container will be named '<code>moodlehost-\<port></code>'. When using a different port value other than the default one you will need to use the same option to stop the server again or purge it's moodledata (see below).

Available commands are:

	moodlehost <options> start: start moddlehost server

	moodlehost <options> stop: stop given moodlehost server

	moodlehost <options> purge: remove all moodledata but the filedir for the given moodlehost server

	<hr>
	v.1.2 2019-11-06
