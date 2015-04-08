## 5. Verify your node's configuration

Now let's log in to your node and run a few commands to help verify that the node is in the expected state. Specifically, we'll verify that the `web_admin` user is set up and that Apache is running and serves your home page.

First, log in to your node over SSH. If you're using a user name and password to authenticate, the command is similar to this.

```bash
# ~/chef-repo
$ ssh ubuntu@52.10.205.36
```

If you're using key-based authentication, the command is similar to this.

```bash
# ~/chef-repo
$ ssh -i ~/.ssh/my.pem ubuntu@52.10.205.36
```

[WINDOWS] Mac OS and most Linux distributions come with an SSH client. On Windows, [PuTTY](http://www.putty.org) is a popular SSH client for logging into Linux machines.

Now that we're logged in, we'll verify that:

* the user `web_admin` exists.
* `web_admin` owns the default home page.
* the `apache2` service is running.
* the home page is in the location we expect.
* the home page is being served and is accessible externally.

### Fetch details for user web_admin

```bash
# ~
$ getent passwd web_admin
web_admin:x:999:1001::/home/web_admin:/bin/bash
```

### Verify that web_admin owns the default home page

```bash
$ stat -c "%U %G" /srv/apache/customers/index.php
web_admin web_admin
```

### Verify that the apache2 service is running

```bash
# ~
$ sudo service apache2 status
 * apache2 is running
```

### Verify that the home page is in the location we expect

```bash
# ~
$ more /srv/apache/customers/index.php
<html>This is a placeholder</html>
```

### Verify that the web page is being served and is accessible externally

First close your SSH session.

```bash
# ~
$ exit
logout
Connection to 52.10.205.36 closed.
```

From your workstation, verify that your web site is accessible. Either navigate to your site from a web browser, or run one of the following commands:

**Mac OS and Linux:**

```bash
# ~
$ curl 52.10.205.36
<html>This is a placeholder</html>
```

**Windows:**

```ps
# ~
$ (Invoke-WebRequest 52.10.205.36).RawContent
HTTP/1.1 200 OK
Accept-Ranges: bytes
Content-Length: 34
Date: Fri, 13 Mar 2015 19:13:30 GMT
ETag: "22-51130067de9ed"
Last-Modified: Fri, 13 Mar 2015 18:54:08 GMT
Server: Apache

<html>This is a placeholder</html>
```