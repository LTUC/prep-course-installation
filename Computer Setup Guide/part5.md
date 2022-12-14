# Part 5
# Postgres Database Installation guide:
- Postgres is an SQL (Relational) Database, we are going to use it during your course, please follow the installation steps carfully

# How to install:
- Open your terminal, and run this command to install the Postgres client and server

```
brew install postgresql
```

- it will take some time to complete ( about 6 mins )
- Once it does, then you can start the server using this command <br>
```
pg_ctl -D /home/linuxbrew/.linuxbrew/var/postgres start
```
- now you should see server started meassage and you can work 
![]()
### Note: you need to start the server each time you reboot your machine, so you will need to run the command again if you are unable to connect
- we can use a shortcut command that will make the proccess easier for you by creating an allias.

``` 
echo 'alias sqlstart="pg_ctl -D /home/linuxbrew/.linuxbrew/var/postgres start"' >> ~/.profile
echo 'alias sqlstop="pg_ctl -D /home/linuxbrew/.linuxbrew/var/postgres stop"' >> ~/.profile
```
`close Ubuntu and run it again`

- now you can easily start the server using this short command <br>
``` sqlstart```  >>> this command will start the server <br>
``` sqlstop```   >>> this command will stop the server

## if you are a Linux User no need to start the server, it will be done automatically
On Linux, postgres can be setup to automatically start when your system reboots, so you do not have to run pgstart every time. To set this up, refer to the Postgres Server Documentation and follow the appropriate instructions for your Linux version to have postgres auto-start as a service.


-------------------------------------------------
## Mac Users
On Mac, we start the postgres server in such a way as to have it run right away, and also re-start itself whenever you restart your computer.

Run this command to enable postgres:

```
brew services start postgres
```

-------------------------------------------------
### How to use:
- Once the server is started
- Create your "user" database and we will need to create a default database for your username by running this command:

``` 
createdb `whoami`
```

- now you should be fine and you just create a database with your default username

- please make sure everything is ok by running psql command:

```
psql
```

- You should see something similar to the following:
```
psql (14.2) // or higher version
Type "help" for help.
yournamehere=#
Type \q to exit the postgres client application and return to your bash shell.
```

<hr>
<h2 align="center"> THE END </h2>
<hr>

<h2 align="center"><a href="part1.md">PART 1</a> | <a href="part2.md">PART 2</a> | <a href="part3.md">PART 3</a> | <a href="part4.md">PART 4</a></h2>
