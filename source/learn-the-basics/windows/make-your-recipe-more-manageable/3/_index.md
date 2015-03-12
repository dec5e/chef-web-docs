## 3. Update the recipe to reference the HTML template

Write out the recipe, <code class="file-path">default.rb</code>, like this.

```ruby-Win32
# ~\chef-repo\cookbooks\learn_chef_iis\recipes\default.rb
powershell_script 'Install IIS' do
  code 'Add-WindowsFeature Web-Server'
  guard_interpreter :powershell_script
  not_if "(Get-WindowsFeature -Name Web-Server).Installed"
end

service 'w3svc' do
  action [:start, :enable]
end

template 'c:\inetpub\wwwroot\Default.htm' do
  source 'index.html.erb'
end
```