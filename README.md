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

Marconi is a general purpose messaging service meant to be used for building distributed systems. Foghorn - on the other hand - is a notification service that's more geared towards the (human) end-user and whose value lies in the

 - integration with other cloud services (which serve as event sources)
 - variety of protocols available to topic subscribers (ideally via pluggable protocol providers)
 - solid support for security roles/rules

According to [Marconi's wiki](https://wiki.openstack.org/wiki/Marconi#Out_of_Scope) it will not support subscriber protocols like email and SMS. The two systems are thus complementary to each other.

## Will Foghorn be built on top of Marconi?

Possibly. Having said that, Foghorn's messaging needs are extremely _simple_ and it's meant to be a foundational service. We'd thus rather avoid dependencies on other services if at all possible.
We are currently thinking of using a [pub-sub](https://en.wikipedia.org/wiki/Publish/subscribe) abstraction module with pluggable backends. One such backend could be Marconi. This would allow for Foghorn deployments that make use of Marconi.
But Foghorn will also have its own _default_ pub-sub backend making stand-alone deployments a possibility.
