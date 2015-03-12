## 5. Ensure the INI file's contents are not changed by anyone else

You need to make sure that no other process can change the INI file.

Imagine that a co-worker manually changes <code class="file-path">settings.ini</code> by replacing 'hello chef' with 'hello robots'. Go ahead and change your copy through your text editor. Or you can change the file from the command line like this.

```ps
# ~\chef-repo
$ Set-Content settings.ini 'greeting=hello robots'
```

Now run `chef-apply`.

```ps
# ~\chef-repo
$ chef-apply hello.rb
Recipe: (chef-apply cookbook)::(chef-apply recipe)
  * file[C:\Users\Administrator\chef-repo\settings.ini] action create
    - update content in file C:\Users\Administrator\chef-repo\settings.ini from 49c070 to cfde92
    --- C:\Users\Administrator\chef-repo\settings.ini    2014-08-12 21:32:38.000000000 +0000
    +++ C:/Users/ADMINI~1/AppData/Local/Temp/settings.ini20140812-1288-1ub7kv2      2014-08-12 21:32:52.000000000 +0000
    @@ -1,2 +1,2 @@
    -greeting=hello robots
    +greeting=hello chef
```

Chef restored the original configuration. This is actually a really good thing because Chef ensures that the actual state of your resource matches what you specify, even if it is altered by some outside process. Chef enables you to both apply a new configuration state as well as ensure that the current state stays how you want it.