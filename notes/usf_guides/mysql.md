mySQL at USF
============

### USF Setup

The general architecture of the mySQL set up at USF is as follows:

<center><img src="images/db2.png" width=600/></center>

mySQL runs on the host `sql.cs.usfca.edu`. 

Servlets (or any other Java program) will use Java Database Connectivity (JDBC) to connect to the database from your Java code.

### Accessing your database via command line

On a lab computer, the following command will connect to your database from a terminal.

`mysql -h sql.cs.usfca.edu -u userXX -p`

The `-h` flag indicates the host. The `-u` flag indicates the user name. *Replace the XX with your assigned id.* The `-p` indicates that a password should be requested. 

### Using Sequel Pro

[Sequel Pro](https://www.sequelpro.com/) is a convenient application that will allow you to browse your database from any computer. It provides a nice graphical interface to allow you to view tables, create tables, and so on.

### Creating an ssh tunnel

If you are off campus you will need to *tunnel* through the firewall to access `sql.cs.usfca.edu` from the command line or from your Java code. 

From the terminal or putty, open an ssh connection as follows:

`ssh -L 3306:sql.cs.usfca.edu:3306 username@stargate.cs.usfca.edu`

This will route all traffic sent to your local port 3306 (the mySQL port) to port 3306 on `sql.cs.usfca.edu` via the secure connection to stargate. Make sure to *replace username with your CS login name*.

In Sequel Pro, if you create an SSH connection it will create the tunnel through the gateway to the server.
