### Rpush
---
https://github.com/rpush/rpush

```
gem 'rpush'
cd /path/to/project
bundle
bundle exec rpush init

cd /path/to/project
rpush start
rpush push
```

```ruby
app = Rpush::Apns::App.new
app.name = "ios_app"
app.certificate = File.read()
app.environment = ""
app.password = "certificate password"
app.connections = 1
app.save!

n = Rpush::Apns::Notification.new
n.app = Rpush::Apns::App.find_by_name("ios_app")
n.device_token = ""
n.alert = ""
n.data = {}
n.save!








```
