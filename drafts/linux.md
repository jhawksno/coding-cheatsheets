#Linux Terminal Reference

## How to find an IP address (Ubuntu)
The following output shows all internet interfaces available, including loopback. 

~~~bash
ip a
~~~

To show just your IP address:

~~~bash
hostname -I
~~~

If you see more than one IP address, you can assume the first one is for the Ethernet interface and the second one is for Wi-Fi interface.

## Change Directories (Linux)

~~~bash
cd path_to_directory
~~~

## Check Working Directory

~~~bash
pwd
~~~

## Create a Directory

~~~bash
mkdir sample/dir
~~~
