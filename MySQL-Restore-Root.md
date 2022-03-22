#Restore Root Privileges if lost. (Extremely Risky!)

##Stop mysqld and restart it with the --skip-grant-tables option
sudo services mysqld stop

sudo vi /etc/mysql/my.cnf

####Add this to the file and save it

\# For debugging and recovery only \#
[mysqld]
skip-grant-tables
skip-networking
\###################################

sudo services mysql restart

###Connect to the mysqld server with just: mysql (i.e. no -p option, and username may not be required).

####Isse the following commands in the mysql client:

UPDATE mysql.user SET Grant_priv='Y', Super_priv='Y' WHERE User='root'; FLUSH PRIVILEGES;

GRANT ALL ON *.* TO 'root'@'localhost';

##If all privileges are restored:
Go ahead and sudo vi /etc/mysql/my.cnf and erase or comment the lines you added and restart mysql service.
