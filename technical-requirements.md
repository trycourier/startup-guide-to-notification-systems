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
| Tracking      | - Can track open rate and click through <br>- deliverability data is dependent on the email server you are sending to <br> - Constantly shifting landscape, what data is available is changing all the time | - Carrier can silently block your delivery so tracking is tricky, tracking click through on links is your best bet <br>- It’s a good idea to build your own domain tracking, otherwise your deliverability can be affected due to the URL shortening service| - You can track engagement as a proxy but there is no way to track real deliverability  | Can track the same way you’d track any other engagement on your website   | - Varies by platform <br> - Slack provides data about if use was online when notification was delivered, click throughs w/hyperlinks or webhook enabled buttons (this requires server side tracking infrastructure)
 |
 
 ## Scalabilty
 
 Very few products have a linear message volume, more likely you will have very spiky times paired with relatively quiet times. This means that queueing and processing messages will be especially important. Below are some best practices to keep in mind when designing your system for scalability.

1. Ensure your queue infrastructure can handle your expected maximum volume (this will prevent a lot of other downstream issues)
2. Latency will be determined by how much time passes between the event that triggers the event and when that event is processed to deliver the message. The listeners that are processing your queue will be the primary bottleneck here though your downstream provider will also constrain your throughput/latency. 
3. Windowing is essential to ensure you are taking advantage of the allotted volume your provider allows without going over, which can result in dropped messages. One strategy for increasing the throughput limitations in place from providers is to have parallel provider accounts or parallel providers. For example, if you use one Twilio account for password resets and a separate Twilio account for transactional notifications you can ensure that if you exceed your limits for transactional notifications it will not affect the deliverability of password resets. Overall the more providers and channels you have at your disposal the less likely you are to saturate your deliverability windows. 



