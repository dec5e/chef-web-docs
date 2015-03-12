## 4. Ensure the MOTD file's contents are not changed by anyone else

You need to make sure that no other process can change the MOTD.

Imagine that a co-worker manually changes <code class="file-path">motd</code> by replacing 'hello chef' with 'hello robots'. Go ahead and change your copy through your text editor. Or you can change the file from the command line like this.

```bash
# ~/chef-repo
$ echo 'hello robots' > motd
```

Now run `chef-apply`.

```bash
# ~/chef-repo
$ chef-apply hello.rb
Recipe: (chef-apply cookbook)::(chef-apply recipe)
  * file[motd] action create
    - update content in file motd from 9b0c18 to b1522f
    --- motd        2014-05-13 15:03:47.638770524 -0700
    +++ /tmp/.motd20140513-4170-130uqxh  2014-05-13 15:04:43.874771326 -0700
    @@ -1,2 +1,2 @@
    -hello robots
    +hello chef
```

Chef restored the original configuration. This is actually a really good thing because Chef ensures that the actual state of your resource matches what you specify, even if it is altered by some outside process. Chef enables you to both apply a new configuration state as well as ensure that the current state stays how you want it.