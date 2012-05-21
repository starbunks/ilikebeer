#Top level Communities folder. This will exist on TESTING, STAGING, DEVELOPMENT (integration) and PRODUCTION.

    Communities/
	    public/
		    wordpress/	#->../deploy/current/wordpress/core/
	    cache/
	    logs/
	    deploy/		# this is the capistrano deployment folder
		    current/	#->symlink to current release
		    releases/	#releases 5 deep
	    uploads/	# contains all uploaded assets
	    bin/		# -> deploy/current/bin/

-----

#Repository contents

    bin/	#Holds any shell type scripts.
    etc/	#Holds all configs.
	    nginx/
		    development/	 #localhost file. This should not be in the repository.
			    wordpress.conf
			    kohana_app.conf
		    production/
			    wordpress.conf
			    kohana_app.conf
		    staging/
			    wordpress.conf
			    kohana_app.conf
		    testing/
			    wordpress.conf
			    kohana_app.conf
	    wordpress/
		    development.php #localhost file. This should not be in the repository.
		    production.php
		    staging.php
		    testing.php
	    kohana/	# This path will be used and set withn the kohana bootstrap.php
		    development/	#localhost file. This should not be in the repository.
		    production/
		    staging/
		    testing/
    wordpress/
	    core/	#Holds the typical wordpress. Only special files and folders noted here.
		    wp-config.php #Copied over from the etc/wordpress/<environment>.php file on deploy.
		    wp-contents/
			    uploads/	#-> ../../../../../uploads/
			    plugins/	#-> ../../../plugins/
			    themes/		#-> ../../../themes/
	    themes/		#Contains *only* needed themes
	    plugins/	#Contains *only* needed plugins
    kohana/
	    system/		#Contains the latest stable version of [kohana](http://kohanaframework.org/)
	    modules/	#All kohana modules go here.
	    applications/	#All kohana applications go here.
		    communities/
			    public/
				    index.php
			    application/	#Kohana application folder with boostrap file.
				    bootstrap.php

-----

#Theme and plugin folder layout

    config/	#Holds any static config files that are specific to the theme. This could be used to pre-populate options for a theme inside the admin.
    assets/
	    images/
	    js/
	    css/
    src/
	    classes/	#Each file within will *only* be php classes. Each file will containt *only* one class and named using the kohana standard.
	    functions/	#Each file within will *only* be php functions. Each file can only contain one function. The file name and function name should be the same. If you need to write more then one function for a solution then write it inside a class.
	    views/		#Use wordpress templates but this would be useful to hold "partials" type views.
	    system/		#This will contain any system type code (all php class files). An autoloader could be here, maybe a simple class to handle loading in views etc.
    sass/		#Holds all the sass files.
    functions.php	#For themes only, This behaves as a bootstrap file and will *never* contain functions or classes. It will only contain code related to loading in files from and organized folder layout within the theme.

-----

#Notes

*Each server that is given a designated environment (PRODUCTION, TESTING, STAGING, DEVELOPMENT) needs to set a bash variable SERVER_ENV set within the bashrc file.
*If no environment variable is set then it will default to DEVELOPMENT.
