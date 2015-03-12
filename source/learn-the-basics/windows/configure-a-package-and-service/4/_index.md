## 4. Confirm your web site is running

Run the `Invoke-WebRequest` PowerShell cmdlet to confirm that your web page is available.

```ps
# ~\chef-repo
$ (Invoke-WebRequest localhost).Content
<html>
  <body>
    <h1>hello world</h1>
  </body>
</html>
```

Optionally, from a web browser on another machine, navigate to your server. You'll see something like this.

![The basic home page](misc/webserver-basic.png)