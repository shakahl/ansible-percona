# Ansible Role: Percona

Ansible playbook to install Percona XtraDB MySQL Cluster on Debian/Ubuntu servers

## Requirements

None.

## Role Variables

Available variables are listed below with its default values.

	mysql_root_password: reallylongpassword
  percona_package: percona-xtradb-cluster-56

Define the MySQL root password, this password will be used to create a **/root/.my.cnf** to allow root mysql connections without password

	port: 3306
	bind_address: 0.0.0.0

Define port and bind address for MySQL connections

	max_allowed_packet: 16M
	key_buffer: 16M
	thread_stack: 192K
	thread_cache_size: 8

Define some values to tuning the database server

	sqldebug: true
	log_slow_queries: log_slow_queries    = /var/log/mysql/mysql-slow.log
	long_query_time: long_query_time      = 2
	log_queries_not_using_indexes: log-queries-not-using-indexes

If **sqldebug** is true this playbook will configure Percona MySQL with slow queries debug logs, if you want to disable this debug information you have to set **sqldebug: false**

	create_app_db: true
	db_name: mydatabase
	db_collation: utf8_general_ci
	db_user: myuser
	db_user_password: anotherreallylongpassword
	db_host: "%"
	db_dump_file: ""

If **create_app_db** is true this playbook will configura an application database, you can set a path for a SQL dump file if you want to restore data in the new application database

## Dependencies

None.

## Example Playbook

	---
	- hosts: all
	  sudo: true
	  roles:
		  - tkuhlman.ansible-percona

## License

MIT / BSD
