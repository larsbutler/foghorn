# What is Foghorn?

Foghorn is a flexible and reliable cloud notification service that can be utilized by both internal services (e.g. monitoring, autoscaling) as well as end-users. Foghorn makes it simple to transmit messages to both human recipients and distributed services.

Foghorn is a cloud service ([reminiscent of SNS](http://aws.amazon.com/documentation/sns/)) facilitating the definition of topics through which messages can be published and consumed in [pub/sub fashion](http://en.wikipedia.org/wiki/Publish–subscribe_pattern) by authorised users.

When subscribing to a topic of interest Foghorn users will specify a protocol (email, http, sms, etc.) through which they wish to consume the posted messages.

Topic owners may define permissions specifying who is allowed to do what for a given topic under what conditions (example: "Joe may subscribe to the 'HighLoad' topic provided he does so via the http protocol").

A message can be customised to have different payloads for each supported protocol e.g. a brief summary for 'sms' and a full content flavour for 'email'.

Moreover Foghorn topics can be combined with other cloud services like monitoring e.g. to allow end users to customise how they want to consume monitoring alerts.

Last but not least users will be able to list the subscriptions for a given topic or all of them.

## API actions

 - add permission
 - confirm subscription
 - create topic
 - delete topic
 - get subscription attributes
 - get topic attributes
 - list subscriptions
 - list subscriptions by topic
 - list topics
 - publish
 - remove permission
 - set subscription attributes
 - set topic attributes
 - subscribe
 - unsubscribe

# Assumptions

 - users will need to confirm a subscription before it takes effect
 - Foghorn will *not* support durable topics i.e. it won't hold messages until consumers subscribe
