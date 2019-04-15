# Hubot-toby

This is the chatbot that lives in the Civic Tech Toronto slack team.

## Commands & Helper Scripts

See [`scripts/`](/scripts) for the set of custom commands/scripts
enabled for our chat bot.

### `calendar-add.coffee`

This command allows any member of our Slack team to easily add events to
[a shared community Google calendar][2] via:

   [2]: https://link.civictech.ca/calendar

```
>>> @ourbot gcal add https://eventbrite.com/xxxxxxxxxxxxx
```

This depends on another small service for parsing event data from urls:
https://github.com/CivicTechTO/event-metadata-parser

For now, this service only knows how to make sense of events on the
EventBrite and Universe platforms, but it could be improved to cover
other platforms.

### `collab-tweeter.coffee`

This script watches for Twitter links in top-level channels, and offered
to RT from organizational account

![screenshot of chat bot offering to tweet](/docs/collab-tweeter-screenshot.png)


### `quicklink-gsheet-lookup.coffee`

This bot command recognizes messages of the format `!keyword` and looks
up the keyword in a designated spreadsheet (like [this one][3]). It
replies with the URL. Using `!!keyword` will reply with a hidden message
than only the user who typed the message will see.

   [3]: https://link.civictech.ca/shortlinks

This relates to a scheduled task that we run, which updates our
shortlinks from this spreadsheet:
https://github.com/civictechto/civictechto-scripts#gsheet2shortlinkspy

### `sms-doorbell.coffee`

We have an internet number set up to notify us our chat channel whenever
someone texts us. We use this as a doorbell at meetups, so that all
organizers can easily take responsibility for answering and dealing with
issues.

It drop the message into a public channel, and the phone number itself
into a private channel, to protect privacy of texters.

(The SMS number is currently attached to @patcon's voip.ms account.)

For Voip.ms documentation on SMS messages, see the "SMS URL Callback"
notes on [the voip.ms wiki][1].

   [1]: https://wiki.voip.ms/article/SMS#Configuring_the_SMS_service
