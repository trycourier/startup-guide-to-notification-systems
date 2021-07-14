## Right User
Ensuring that your notifications are going out to the right user is table stakes.  Ensuring that your user events are properly wired up with the relevant data associated with them is the most important piece to getting this right.

*Example: If a new user is added to the account of a B2B SaaS app, should the billing admin be notified? How about the other admins? You need to ensure that your events are properly wired so that this single sign-up event can trigger any relevant notifications and include the relative data to that notification.*

## Right Message
The user needs to be in control of ensuring they only get the notifications that they care about and through their preferred channel(s). It’s your job as the developer to  provide sane defaults to make this job easy on the user. 

*Example: If your application has 25 different possible notifications, don’t ask the user to toggle each one of those on/off plus set channel preferences. Rather, you should group them into logical groups and then allow the user to decide when and how they want to receive each group of notifications.*

## Right Frequency
Notifications that are too frequent annoy users and hurt engagement. However, missing an essential notification can potentially ruin the utility of a product for a user.

*Example: When you get five messages while you are away on Slack, Slack does not send you five notifications. Rather it batches those five notifications into a single ‘While you were away’ notification. Your system should have the ability to batch notifications in order to avoid over-notifying users and should have access to all relevant events in order to make sure your user’s don’t miss anything important.* 

## Right Channel
The channel requirements for each product will differ depending on the user’s preferred communication methods. No matter what channels you need to support, your notification system needs the flexibility to respect your user’s preferences and deliver each type of notification to the channel of choice for each individual user. You should also design your system with the flexibility to support other channels in the future that you may not need today.

*Example: Your users may want to receive certain notifications over email only, others over email + Slack, and still others over Slack only. You should make sure this is easy to customize while providing sane defaults to start out.* 

## Right Time
Timing is perhaps the most important aspect of delivering effective notifications. A well timed notification delights users, while a poorly timed one annoys or angers them. Your notification system needs the flexibility to adjust sends based on the time of day where your user is, the actions your user has taken, and the relevant job your user is trying to achieve.

*Example: A B2B IT management application sends an admin an email when a user requests permission to create a new Slack channel. If there is no response within 2 business days, it follows up with a Slack notification to that admin during business hours. If another 2 business days pass with no response, it sends another email to both the admin and the requester notifying them that the request has expired without being granted.*
