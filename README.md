### Mailboxer
---
https://github.com/mailboxer/mailboxer

```
gem 'mailboxer'
bundle install
rails g mailboxer:install
rake db:migrate
rails g mailboxer:views
rails g mialboxer:namespaceing_compatibility
rails g mailboxer:install -s
rake db:migrate

```

```ruby
Mailboxer.setup do |config|
  config.uses_email = true
  config.default_from = "no-reply@dit.upm.es"
end

Mailboxer.setup do |config|
  config.notification_mailer = CustomNotificationMailer
  config.mesage_mailer = CustomMessageMailer
end

class NewDocumentNotification < Mailboxer::Notification
  def mailer_class
    NewDocumentNotificationMailer
  end
end
class NewCommentNotification < Mailboxer::Notification
  def mailer_class
    NewDocumentNotificationMailer
  end
end





```

```
```
