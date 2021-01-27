# **Installation and Configuration**

1. Install mysql server - <br />
  *guri@guri-Notebook:~$ sudo apt-get install mysql-server*

2. Configure mysql server - <br />
  *guri@guri-Notebook:~$ sudo mysql_secure_installation* <br />
    Enter the details accordingly as per your requirement.
    
3. Enable Firewall - <br />
  *guri@guri-Notebook:~$ sudo ufw enable* 

4. Allow mysql in firewall - <br />
  *guri@guri-Notebook:~$ sudo ufw allow mysql* 

5. Start mysql server - 
  *guri@guri-Notebook:~$ sudo systemctl start mysql*

6. Whitelist your local-server on - <br />
  *guri@guri-Notebook:~$ sudo vi /etc/mysql/mysql.conf.d/mysql.cnf* <br />
  [Bind IP in this file]

# **login** <br />
1. *guri@guri-Notebook:~$ mysql -u root -p <br />*
    then enter the password that you provided during configuration.

2. create user - <br />
  *mysql> create user 'guri'@'localhost' identified by 'abc';*

3. Grant all permissions to the user -  <br />
  *mysql> GRANT ALL PRIVILEGES ON *.* TO 'guri'@'localhost';*

4. Activate privileges - <br />
  *mysql> Flush privileges;* 
  [exit the mysql console]

5. now login with the user that we created from the Terminal - <br />
   *guri@guri-Notebook:~$ mysql -u guri -p*

5. create database - <br />
  *mysql> create database testdb;*

6. use the testdb database - <br />
  *mysql> use testdb;*
 
7. now create the table - <br />
  *create table Contact(
  Firstname varchar(255),
  Lastname varchar(255),
  Phone varchar(12),
  Mobile varchar(12),
  email varchar(255)
);*

8. *mysql> describe Contact;* <br />
<pre>
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| Firstname | varchar(255) | YES  |     | NULL    |       |
| Lastname  | varchar(255) | YES  |     | NULL    |       |
| Phone     | varchar(12)  | YES  |     | NULL    |       |
| Mobile    | varchar(12)  | YES  |     | NULL    |       |
| email     | varchar(255) | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
</pre>


9. inserting data into table - <br />
  *insert into Contact (Firstname, Lastname, Phone, Mobile, email) values ("gurjeet","singh","123456789","123456","gurjeetbhari@gmail.com");*

10. *select * from Contact;*
<pre>
+-----------+----------+-----------+--------+------------------------+
| Firstname | Lastname | Phone     | Mobile | email                  |
+-----------+----------+-----------+--------+------------------------+
| gurjeet   | singh    | 123456789 | 123456 | gurjeetbhari@gmail.com |
+-----------+----------+-----------+--------+------------------------+
</pre>

10 alter table (adding new col) - <br />
 *mysql> alter table Contact add address varchar(255);*
 <pre>+-----------+----------+-----------+--------+------------------------+---------+
| Firstname | Lastname | Phone     | Mobile | email                  | address |
+-----------+----------+-----------+--------+------------------------+---------+
| gurjeet   | singh    | 123456789 | 123456 | gurjeetbhari@gmail.com | NULL    |
+-----------+----------+-----------+--------+------------------------+---------+
</pre>
