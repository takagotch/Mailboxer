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

def name
  return "You should add method :name in your Messageable model"
end

def mailboxer_email(object)
  # if true
  return "define_email@on_your.model"
  # return nil
end

Mailboxer.setup do |config|
  config.email_method = :mailboxer_email
  config.name_method = :name
  config.notify_method = :notify
end

config.email_method = :notification_email
config.name_method = :display_name
config.notify_method = :notify_mailboxer

class User < ActiveRecord::Base
  acts_as_messageable
end







```

```
```
