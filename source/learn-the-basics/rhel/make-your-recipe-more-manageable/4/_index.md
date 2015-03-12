## 4. Run the cookbook

Now run the cookbook. To do so, we use the `chef-client` command and specify what's called the _run-list_.

```bash
# ~/chef-repo
$ sudo chef-client --local-mode --runlist 'recipe[learn_chef_httpd]'
[2014-07-28T20:05:38+00:00] WARN: No config file found or specified on command line, using command line options.
Starting Chef Client, version 11.16.0
resolving cookbooks for run list: ["learn_chef_httpd"]
Synchronizing Cookbooks:
  - learn_chef_httpd
Compiling Cookbooks...
Converging 3 resources
Recipe: learn_chef_httpd::default
  * package[httpd] action install (up to date)
  * service[httpd] action start (up to date)
  * service[httpd] action enable (up to date)
  * template[/var/www/html/index.html] action create
    - update content in file /var/www/html/index.html from 2914aa to ef4ffd
    (no diff)
    - restore selinux security context
  * service[iptables] action stop (up to date)

Running handlers:
Running handlers complete
Chef Client finished, 1/5 resources updated in 5.902863207 seconds
```

[COMMENT] You ran `chef-apply` to run a single recipe from the command line. `chef-client` is what you use to run a cookbook.

Run `curl` again or refresh your web browser to confirm that your web page is still available.

```bash
# ~/chef-repo
$ curl localhost
<html>
  <body>
    <h1>hello world</h1>
  </body>
</html>
```

The result is the same as before, but with a cookbook things are now easier to manage.