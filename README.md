AutoMySQLBackup
===============
 A fork and further development of AutoMySQLBackup from sourceforge. http://sourceforge.net/projects/automysqlbackup/ 
 
Information
-----------

Creating backups means copy the data in a way where it can be restored again. To backup a mysql database server in most cases it is needed to create a dump from the database and each table. If the data, mysql stores in its data directory is simply copied, restoring the data in the mysql database will not be possible. This command line tool enables you to create and maintian mysql backups. You can backups of innodb and myisam tables.

Automysqldumper uses mysqldump for creating the sql backup. By default databases are backed up in separate gzipped files. To restore a database you can use:

```
zcat daily_andi_wiki_2016-12-24_03h59m_Saturday.sql.gz | mysql -u root -p
```

Change the name of the file to your needs. After this simple step you get back the data into your database.

To setup this script have a look at the automysqlbackup.conf file. In there you have several options to configure the mysql backup script to your needs.

Adjustments
-----------

You can find some original files from the sourceforge package. Some files are adjusted to my needs:
- support for MySQL 5.6 and MySQL 5.7
- support for login path (since MySQL 5.6.x a secure way to save your mysql credentials was implemented)
- adjusted the use of --ssl because it became depreated in MySQL 5.7. The parameter --ssl-mode=REQUIRED is used instead.

Add login path
--------------
Per default this script uses the login path automysqldump.

```
mysql_config_editor set --login-path=automysqldump --host=localhost --user=root --password
```

After that command give your mysql root password and you're done. If you want to do your backup with another user, simply change the username.


Backup your mysql server with ease by using this adjusted script. If you encounter any errors feel free to [drop an issue](https://github.com/sixhop/AutoMySQLBackup/issues/new). :) (English or German)

For more Information check out [managed hosting by sixhop.net](http://www.sixhop.net/).
