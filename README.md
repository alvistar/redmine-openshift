Redmine on OpenShift
=========================

Redmine is a flexible project management web application. Written using Ruby on Rails framework, it is cross-platform and cross-database.

Redmine is open source and released under the terms of the GNU General Public License v2 (GPL).

More information can be found on the official Redmine set (www.redmine.org)
Running on OpenShift
--------------------

Create an account at https://www.openshift.com

Create a ruby application

	rhc app create redmine ruby-1.9 mysql-5.1 

Make a note of the username, password, and host name as you will need to use these to login to the mysql database

Add this upstream Redmine quickstart repo

	cd redmine
	git remote add upstream -m master https://github.com/alvistar/redmine-openshift.git
	git pull -s recursive -X theirs upstream master

This will disable xapian gem (needed for fulltext search)

	rhc env set BUNDLE_WITHOUT=xapian

Then push the repo upstream

	git push

That's it, you can now checkout your application at:

	http://redmine-$yournamespace.rhcloud.com


Use the following to login to your new Redmine application running on OpenShift:

	username: admin
	password: admin


Changing the default admin password
-----------------------------------
Once your installation is complete, it is highly recommended that you change
the password for the Redmine admin user - see the Change password link at:

	http://redmine-$yournamespace.rhcloud.com/my/account

Version
-----------------------------------
Redmine 2.5
