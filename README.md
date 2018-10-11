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
app.certificate = File.read("/path/to/sandbox.pem")
app.environment = "development"
app.password = "certificate password"
app.connections = 1
app.save!

n = Rpush::Apns::Notification.new
n.app = Rpush::Apns::App.find_by_name("ios_app")
n.device_token = "..."
n.alert = "hi!"
n.data = {　foo: :bar }
n.save!

app = Rpush::Apnsp8::App.new
app.name = "ios_app"
app.apn_key = File.read("/path/to/sandbox.p8")
app.environment = "development"
app.apn_key_id = "APN KEY ID"
app.team_id = "TEAM ID"
app.bundle_id = "BUNDLE ID"
app.connections = 1
app.save!

n = Rpush::Apns::Notification.new
n.app = Rpush::Apnsp8::App.find_by_name("ios_app")
n.device_token = "..."
n.alert = "hi!"
n.data = { foo: :bar }
n.save!

app = Rpush::Gcm::App.new
app.name = "android_app"
app.auth_key = "..."
app.connections = 1
app.save!

n = Rpush::Apns::Notification.new
n.app = Rpush::Apnsp8::App.find_by_name("android_app")
n.registration_ids = ["..."]
n.date = { message: "hi!" }
n.priority = 'high'
n.content_available = true
n.notification = { body: 'great match!',
                   title: 'Portugal vs. Denmark',
                   icon: 'myicon'
                  }
n.save!

app = Rpush::Adm::App.new
app.name = "kindle_app"
app.client_id = "..."
app.client_secret = "..."
app.connections = 1
app.save!

n = Rpush::Adm::Notification.new
n.app = Rpush::Adm.find_by_name("kindle_app")
n.registration_ids = ["..."]
n.data = { message: "hi!" }
n.collapse_key = "Optional consolidationKey"
n.save!

app = Rpush::Wpns::App.new
app.name = "windows_phone_app"
app.client_id = #https://dev.windows.com
app.client_secret = #https://dev.windows.com
app.connections = 1
app.save!

n = Rpush.Wpns::Notification.new
n.app = Rpush::Wpns::App.find_by_name("windows_phone_app")
n.uri = "http://..."
n.data = {title:"MyApp", body:"Hello world", param:"user_param1"}
n.save!

app = Rpush::Wns::App.new
app.name = "windows_phone_app"
app.client_id = YOUR_SID_URL
app.client_secret = YOUR_CLIENT_SECRET
app.connections = 1
app.save!

n = Rpush::Wns::Notification.new
n.app = Rpush::Wns::App.find_by_name("windows_phone_app")
n.uri = "http://..."
n.data = {title:"MyApp", body:"Hello world", launch:"launch-argument"}
n.sound = "ms-appx:///mynotificationsound.wav"
n.save!

n = Rpush::Wns::RawNotification.new
n.app = Rpush::Wns::App.find_by_name("windows_phone_app")
n.uri = 'http://...'
n.data = { foo: 'foo', bar: 'bar' }
n.save!

n = Rpush::Wns::BadgeNotification.new
n.app = Rpush::Wns::App.find_by_name("windows_phone_app")
n.uri = 'http://...'
n.badge = 4
n.save!

app = Rpush::Pushy::App.new
app.name = "android_app"
app.api_key = YOUR_API_KEY
app.connections = 1
app.save!

n = Rpush::Pushy::Notification.new
n.app = Rpush::Pushy::App.find_by_name("android_app")
n.registration_ids = ["..."]
n.data = { message: "hi!" }
n.time_to_live = 60
n.save!

Rpush.push
Rpush.apns_feedback

if definded?(Rails)
  ActiveSupport.on_load(:after_initialize) do
    Rpush.embed
  end
else
  Rpush.embed
end







```
