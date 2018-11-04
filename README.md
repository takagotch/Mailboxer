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

class Duck < ActiveRecord::Base
  acts_as_messageable
end

class Cylon < AcitveRecord::Base
  acts_as_messageable
end

alfa.send_message(beta, "Body", "subject")

conversation = alfa.mailbox.inbox.first
receipts = conversation.receipts_for alfa
receipts.each do |receipt|
  message = receipt.message
  read = receipt.is_unread? # message.is_unread?(alfa)
end

alfa.reply_to_all(receipt, "Reply body")
alfa.reply_to_conversation(conversaton, "Reply body")

alfa.reply_to_sender(receipt, "Reply body")

receipt.mark_as_deleted

conversation.mark_as_deleted participnt

alfa.mark_as_deleted conversation

conversation.messages_for(alfa)

alfa.mailbox.conversations
alfa.mailbox.info
alfa.mailbox.sentbox
alfa.mailbox.trash

conversations = alfa.mailbox.conversations.page(params[:page]).per(9)
conversations = alfa.mailbox.info.page(params[:page]).per(9)
conversations = alfa.mailbox.sendbox.page(params[:page]).per(9)
conversations = alfa.mailbox.trash.page(params[:page]).per(9)
```

```
```
