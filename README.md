MySQL-AutoXtrabackup
====================

MySQL AutoXtrabackup commandline tool written in Python 3.
For community from Azerbaijan MySQL User Community: [MySQL Azerbaijan Community](http://mysql.az/about/).
For any question please ask: [Email](mailto:rzayev.shahriyar@yandex.com)

===========

Demo Usage Video(is subject to change):
--------------------------------------

[![autoxtrabackup tool usage demo video](http://img.youtube.com/vi/ZGAODq4MVWc/0.jpg)](https://www.youtube.com/watch?v=ZGAODq4MVWc)


Requirements:
-------------

    * Percona Xtrabackup (>= 2.2.10)
    * Python 3 (tested version 3.3.2)
    * Official mysql-connector-python (>= 2.0.2 )
    * Python Click package (>= 3.3)
    * mysql-utilities (>=1.5.4)

===========

Preparing System
-----------------

    Installing dependencies:

        yum install openssl openssl-devel zlib zlib-devel
        
    Installing latest XtraBackup:
        
        yum install http://www.percona.com/downloads/percona-release/redhat/0.1-3/percona-release-0.1-3.noarch.rpm
        yum install percona-xtrabackup

    Installing Python 3 from source:

        wget https://www.python.org/ftp/python/3.3.2/Python-3.3.2.tar.bz2
        tar -xvf Python-3.3.2.tar.bz2
        cd Python-3.3.2
        
        -- Open Setup.dist file and search for zlib, uncomment zlib notes:
        * nano Modules/Setup.dist
        # See http://www.gzip.org/zlib/
        zlib zlibmodule.c -I$(prefix)/include -L$(exec_prefix)/lib -lz

        -- Also search for ssl and uncomment ssl section:
        
        # socket line above, and possibly edit the SSL variable:
        SSL=/usr/local/ssl
        _ssl _ssl.c \
	            -DUSE_SSL -I$(SSL)/include -I$(SSL)/include/openssl \
                -L$(SSL)/lib -lssl -lcrypto

        mkdir /opt/Python-3.3.2
        ./configure --prefix=/opt/Python-3.3.2

        make
        make install
    
    
    Installing setuptools:
    
        wget https://pypi.python.org/packages/source/s/setuptools/setuptools-15.1.tar.gz#md5=10407f6737d8dc37e5310e68c1f1f6ec
        tar -xvf setuptools-15.1.tar.gz
        cd setuptools-15.1/
        python3 setup.py install
    
    Installing pip:
        
        wget https://pypi.python.org/packages/source/p/pip/pip-7.1.2.tar.gz#md5=3823d2343d9f3aaab21cf9c917710196
        tar -xvf pip-7.1.2.tar.gz
        cd pip-7.1.2
        python3 setup.py install 
    
    Installing MySQL-AutoXtrabackup and dependencies:
        
        cd /home
        git clone https://github.com/ShahriyarR/MySQL-AutoXtraBackup.git
        cd  /home/MySQL-AutoXtraBackup/
        python3 setup.py install
    

        
Project Structure:
------------------
    
    XtraBackup is powerful and open-source hot online backup tool  for MySQL from Percona.
    This script is using XtraBackup for full and incremental backups, also for preparing and recovering taken backups
    Here is project path tree (default location is /home/MySQL-AutoXtraBackup):
        
        * backup_dir 			-- The main folder for storing backups.
        * master_backup_script	-- Full and Incremental backup taker script.
        * backup_prepare		-- Backup prepare and restore script.
        * partial_recovery		-- Partial table recovery script.
		* general_conf			-- All-in-one config file's and config reader class folder.
    	* setup.py				-- Setuptools Setup file.
    	* autoxtrabackup.py		-- Commandline Tool provider script.
    	* /etc/bck.conf         -- Config file will be created from general_conf/bck.conf

============


Usage:
-----
        1. Clone repository to local directory. 
        2. Install using setup script.
        3. Edit /etc/bck.conf file reflecting your settings and use.
		
		
		* Please see Demo Usage Video.
		