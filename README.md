# __Useful linux commands for system admins or for application trobulshooting__ 

1. ##__curl__

__command line url__ transfers an URL to test an application endpoint or connectivity to an upstream service endpoint . curl can be useful to check if your application can reach to another service/port or not . such as a database or checking the service is healthy or not .

``` 
$curl -I -s myapp:3000
HTTP/1.0 500 INTERNAL SERVER ERROR
```:bash

The -I tag shows the header info and the -s tag silence the response body . checking the endpoint of our database .

```
$curl -I -s databse:27017
HTTP/1.0 200 ok
```:bash

so what could be the problem check if your application can reach to another places besides from the database check from the application host
```
$curl -I -s http://opensource.com
HTTP/1.0 200 ok
```

Now try to reach the database from the databse host 
```
$curl database:27017
could not resolve host 
```

This seems like the database url is un available or the host name is wrong .

2. ##__python -m json.tool__

if you are dealing with servers then the output of the API call may be hard to read or debug sometimes we want to pretty print the output. python has a inbuilt json library to do so .

```
$cat test.json 
```

```
$cat test.json | python -m json.tool 
```

3. ##__env__
__env__ allows us to set or point the environment variables . During troubleshooting you may find it useful for checking if wrong environment variable prevents your application from starting . 

4. ##__netstat__
__netstat__ used for checking the network status like checking the ports in use and their incomming connections .
As a developer if you are pushing your application onto the localhost or remote you might come accross the error __port is already allocated__ by using certion flags we can caheck which port is allocated to which application .
```$netstat -tulpn```

5. ##__namp__
__network security__ is as important to every person who are serfing web in todays so nmap is a powerful cmd tool used for scanning our network . 


6. ##__netcat__
__netstat__ is a powerful tool for establish the conection between two hosts/machines over the network . It can be used as a reverse shell .


7. ##__dig/nslookup__
A domain name server helps resolve a url in a set of application servers . however  you may find that a url does not resove error . Insted we can use use dig or nslookup commands to check the reason 

```$nslookup mydatabase ```

```$dig mydatabase ```

8. ##__df__
__disply the free disk space__ to troubleshoot the disk space issue .  When we are running multiple vms on single host it is necessasry for a system admin to manage the disk space .

```
$df -h 

or if you are wanted the info about a specific dir

$df -h /home
```

9. ##__du__
To retrive more detailed info about which files uses the max disk space we can use disk usages utility.

```$du -sh /var/log/*```

10. ##__lsof__
__lists the open file__ associated with your application . If your application writes to a file or open a network connection lsof can be used to reflect that iformation . similar to netstat .

```$lsof -i tcp:80```

------------------------More Commands added soon -----------------------