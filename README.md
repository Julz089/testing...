Setup bare gitweb repository
==============

https://wiki.archlinux.org/index.php/Gitweb

*Adding repositories*
--------------

	mkdir my_repository.git
	git init --bare my_repository.git/
	cd my_repository.git/
	touch git-daemon-export-ok
	echo "Short project's description" > description

*Add markdown hook*
--------------
**my_repository.git/hooks/post-receive**

	#!/bin/sh
	#
	# Post-receive hook script which generates README.html to git-dir from
	# README.md found at the head of master branch in repository.
	#
	# Gitweb can read the README.html and embed it to the project summary page.

	git cat-file blob HEAD:README.md | markdown > $GIT_DIR/README.html


	
Dependencies
--------------

- mod_perl
- perl_cgi
