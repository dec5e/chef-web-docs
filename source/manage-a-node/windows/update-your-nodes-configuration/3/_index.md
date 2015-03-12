## 3. Run the cookbook on your node

<div id="knife-intro" class="indent" data-type="windows-fundamentals" ng-non-bindable>
Run <code>knife winrm</code> to run your cookbook on your node. Replace <code>{{address}}</code>, <code>{{user}}</code>, and <code>{{password}}</code> with your values.
</div>
<p/>
<div id="knife-command" class="window" ng-non-bindable>
  <nav class="control-window">
    <div class="close">&times;</div>
    <div class="minimize"></div>
    <div class="deactivate"></div>
  </nav>
  <h1 class="titleInside">Terminal: ~/chef-repo</h1>
  <div class="container" data-type="windows-fundamentals"><div class="terminal"><table>
    <tbody>
      <tr>
        <td class="gutter"><pre class="line-numbers"><span class="line-number">$</span></pre></td>
        <td class="code"><pre><code><span class="line command">knife winrm {{address}} chef-client --manual-list --winrm-user {{user}} --winrm-password '{{password}}'</span></code></pre></td>
      </tr>
    </tbody></table></div></div>
</div>

[COMMENT] In production, you'll likely configure `chef-client` to run automatically on a regular basis or in response to some event or trigger, such as when code is checked in to your repository. But for now, we'll update our server configuration by running `chef-client` manually.