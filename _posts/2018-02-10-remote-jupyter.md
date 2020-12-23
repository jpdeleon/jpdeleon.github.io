---
layout: post
title: Remote jupyter
#subtitle:
bigimg: /img/2018-02-10-img1.jpeg
tags: [jupyter, linux, blog]
comments: true
css: /css/jupyter.css
---

# Working with jupyter server remotely

I normally set-up my desktop as a server and my laptop as a client. Jupyter notebook can be run in a remote server
which can be edited locally in a client's browser. In this way, the computing resources of my desktop is utlized with
the convenience of working on a laptop.

We will do this by opening an SSH tunnel.
This tunnel will forward the port used by the Jupyter kernel running on remote server to a port on the local machine,
where it can be accessed in a browser just like running Jupyter in your local computer.

## Setting up jupyter in a remote server
In your remote server, launch jupyter notebook without browser
```bash
[remote-server@user] $ jupyter notebook --no-browser
```

## Using jupyter notebook and viewing it on your local browser

1. From your local computer, connect to the Jupyter kernel running on s remote server via ssh tunnel
with the format: ssh -L remote_host:remote_port:localhost:locat_port

```bash
$ ssh -L localhost:8888:localhost:8889 <remote-server>
```
where 8888 is your local browser's (unused) port number and 8889 is remote's port number currently used by Jupyter.

If you see a message saying:
```
> (bind) port already in use
```

That means 8888 is not available (may be you have other jupyter kernel running locally), so you can try 8889, 8890, and so on.
I'll use 9999:
```bash
$ portnumer = 9999
$ ssh -L localhost:$portnumber:localhost:8889 <remote-server>
```

Note that you can check which port number is being used:
```bash
$ jupyter notebook list
```

2. To view remote jupyter server using your local browser, go to:

> localhost:9999

3. If asked for a token (usually for first time users), run the command in ssh session.
```bash
[remote-server@user]$ jupyter notebook list
```

Example output:
```bash
Currently running servers:
http://localhost:9999/?token=6bb0d3427636d0f0802fd1b6eeacaa9f84e9326cfe7fb1c7 :: /home/usr
```
Copy 6bb0d3427636d0f0802fd1b6eeacaa9f84e9326cfe7fb1c7 and paste it in your browser.

4. To avoid ssh disconnection, run `htop` in ssh session and leave it as it is:
```bash
[remote-server@user] htop
```

5. To quit Jupyter notebook, first check the process id:
```bash
$ ps aux | grep localhost:9999
```

Sample output:
23295  0.0  0.0  50064  6608 pts/2    S+   16:32   0:00 ssh -L localhost:9999:localhost:8889 <remote-server>

Then kill the process in your local pc:
```bash
$ kill 23295
```

Finally, you can disconnect from ssh session in the usual way.
First, quit htop by pressing <q> key and then type <exit> in the remote server terminal.

For convenience, I add the following in my ~/.alias sourced in ~/.bashrc:
```bash
portnumber=9999
alias ssh_jup="echo 'using local port number=' $portnumber && ssh -L localhost:$portnumber:localhost:8889 <remote-server>"
```
