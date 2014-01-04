Relatinal database publisher.
=============================

Getting Started.
------------------------------

### Odbc configuration on Ubuntu ###
*** Based on:*** skubuntu.com/questions/167491/connecting-ms-sql-using-freetds-and-unixodbc-isql-no-default-driver-specified

### Install unixodbc and freetds ###
	sudo apt-get install unixodbc unixodbc-dev freetds-dev tdsodbc

* and configure freetds as follows:
	--- /etc/freetds/freetds.conf ---
	[TS]
	host = SERVER
	port = 1433
	tds version = 7.0
	client charset = UTF-8

* install tsql
    sudo apt-get install freetds-bin

* validate tsql
    tsql -S SERVER -U User -P Password


* verify odbc setting
    odbcinst -j

* My output was because I previously installed unixODBC 2.3.0 driver according the following recomendations:
    *** http://www.bardiak.com/2012/09/installing-ms-sql-server-driver-on.html

    unixODBC 2.3.0
	DRIVERS............: /usr/local/etc/odbcinst.ini
	SYSTEM DATA SOURCES: /usr/local/etc/odbc.ini
	FILE DATA SOURCES..: /usr/local/etc/ODBCDataSources
	USER DATA SOURCES..: /home/andrei/.odbc.ini
	SQLULEN Size.......: 8
	SQLLEN Size........: 8
	SQLSETPOSIROW Size.: 8

### Edit odbcinst.ini ###
    [FreeTDS]
    Description = FreeTDS
    Driver = /usr/lib/x86_64-linux-gnu/odbc/libtdsodbc.so
    client charset = utf-8


### Edit odbc.ini ###
    [TS]
	Description = "test"
	Driver = FreeTDS
	Server = SERVER
	Port = 1433
	Database = DATABASE











