##Ansible-wordpress

This is an Ansible playbook to install wordpress on amazon linux. This will also install lamp on the ec2 server. In this playbook we are using prompt to input variables.


***

***


#### Template File

	# vim virtualhost.j2
	<virtualhost *:80>
	    servername {{domain}}
	    documentroot /var/www/html/{{domain}}
	    directoryindex index.html index.php
	</virtualhost>



***

***

####wp-config.php.j2

		<?php
		
		/** The name of the database for WordPress */
		define( 'DB_NAME', "{{mysql_database}}" );
		
		/** MySQL database username */
		define( 'DB_USER', "{{mysql_user}}" );
		
		/** MySQL database password */
		define( 'DB_PASSWORD', "{{mysql_password}}" );
		
		/** MySQL hostname */
		define( 'DB_HOST', 'localhost' );
		
		/** Database Charset to use in creating database tables. */
		define( 'DB_CHARSET', 'utf8' );
		
		/** The Database Collate type. Don't change this if in doubt. */
		define( 'DB_COLLATE', '' );
		
		
		define( 'AUTH_KEY',         'put your unique phrase here' );
		define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
		define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
		define( 'NONCE_KEY',        'put your unique phrase here' );
		define( 'AUTH_SALT',        'put your unique phrase here' );
		define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
		define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
		define( 'NONCE_SALT',       'put your unique phrase here' );
		
		
		$table_prefix = 'wp_';
		
		
		define( 'WP_DEBUG', false );
		
		
		if ( ! defined( 'ABSPATH' ) ) {
			define( 'ABSPATH', dirname( __FILE__ ) . '/' );
		}
		
	require_once( ABSPATH . 'wp-settings.php' );