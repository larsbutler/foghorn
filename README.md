# What is Foghorn?

Foghorn is a flexible and reliable cloud notification service ([reminiscent of SNS](http://aws.amazon.com/sns/)) facilitating the definition of topics through which messages can be published and consumed in [pub/sub fashion](http://en.wikipedia.org/wiki/Publish–subscribe_pattern) by authorised users.

It can be utilized by other cloud services (e.g. monitoring, autoscaling) or arbitrary systems to publish information of interest. Foghorn makes it simple to pass messages to both human recipients and distributed services.

When subscribing to a topic of interest Foghorn users will specify a protocol (email, http, sms, etc.) through which they wish to consume the posted messages.

Topic owners may define permissions specifying who is allowed to do what for a given topic under what conditions (example: "Joe may subscribe to the 'HighLoad' topic provided he does so via the http protocol").

A message can be customised to have different payloads for each supported protocol e.g. a brief summary for 'sms' and a full content flavour for 'email'.

Last but not least users will be able to list the subscriptions for a given topic or all of them.

The aim is to develop this project together with the OpenStack community and eventually make it an integral part of OpenStack.

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

# FAQ

## How is Foghorn different from Marconi?

Marconi's current focus is on point-to-point queues. It's primarily orientated toward developers who are building distributed systems.
Foghorn - on the other hand - is envisioned as a (pub-sub style) notification service that's more geared towards the (human) end-user and whose value will lie in

 - integration with other cloud services (which serve as event sources)
 - variety of protocols available to topic subscribers (ideally via pluggable protocol providers)
 - solid support for security roles/rules

## Will Foghorn be built on top of Marconi?

Marconi is an OpenStack umbrella project for messaging and Foghorn fits thematically very well (pub-sub, notifications).
In order to save effort when it comes to code and community development and to share expertise and know-how Foghorn will be pursued as part of Marconi.
If and when Foghorn grows too big it can always be spun off into a separate project.
