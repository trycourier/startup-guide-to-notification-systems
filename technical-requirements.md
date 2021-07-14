# Technical Requirements
![Technical Requirements Illustration](img/technical-requirements.jpg?raw=true)

## Reliability
The first thing to recognize when it comes to the reliability of a notification systems is that, by definition, you will be using third party services (Twilio, MailGun, PostMark, etc) who’s uptime and reliability you cannot control. At some point one of these services will be down and how your system handles that down time is central to it’s reliability. 

There are three core factors that must be thought through from a technical perspective when designing the system for reliability.
 
1. Idempotency: you need to ensure that each notification will only be delivered once. Redundant notifications are a great way to annoy and lose users.
2. Fail over: What is your backup plan? Do you have a different provider you can fall back on if one is down? Or maybe an alternate delivery channel (e.g. fallback to push or SMS when email is down)? This will likely depend on each individual message type and will require some sophisticated mapping.
3. Timeliness: some messages are only useful if delivered within minutes, others within hours, and others within days. You need to decide, on a per message basis, at which point it actually makes more sense to drop the message then to deliver it.

*Example: Say your email notification provider went down for half an hour. Some users who requested a password reset during this time hit the request link multiple times because they never received the reset email. When your email system is back up, you don’t want to send them a bunch of redundant password reset emails, you only want to send them the most recent one and drop the others.*

## Deliverability
When it comes to notification systems, deliverability is essential. A message that does not make it to its intended destination will almost certainly fail in achieving its goal and can have devastating consequences for the customer. Optimizing and tracking deliverability differ dramatically by channel. 

| Channel      | Email | SMS      | Mobile Push  | In App      | Slack/Chat |
| -----------  | ----------- | ----------- | ----------- | ----------- | ----------- |
| Optimization      | - SPF, DKIM, and DMARC need to be in place to avoid spam filters -  cross-client email testing/preview <br>| - If you are sending at scale you need to use multiple numbers to ensure you’re not blocked by the provider <br>- Regional pricing varies greatly, vendor support for various regions varies as well | - Typically as your volume of mobile push notifications goes up deliverability will go down as users will revoke push permissions <br> - Best thing you can do here is to make each notification as useful and timely as possible <br> - You can optimize the process of asking for permission but not actual deliverability <br> - iOS is introducing message batching this fall which will change the UX of iPhone push notifications (based on ML) | - Basic web development user experience, ensure you test on different devices and browsers <br> - Many 3rd party notification services are blocked by ad blocking services | - Authentication and permissioning are complex, it’s best to adhere to that particular chat platforms best practices to ensure deliverability 

| Tracking      | Email | SMS      | Mobile Push  | In App      | Slack/Chat |

