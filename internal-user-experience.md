# Internal User Experience Requirements
![Intro Illustration](img/internal-user-experience.jpg?raw=true)

## API First
The nature of application-human-communication (aka notifications) is that they will need to be triggered from code. Because of this it’s important that as many features as possible that you offer in your system are able to be performed via that API.

*Example: While today your only notification use case may be a simple email, as your product grows more sophisticated additional notification use cases will almost certainly surface. A good API is the best way to ensure you will be able to execute on use cases you have not yet defined.*


## Great Documentation
It’s important that both your engineering team and non-technical users are able to effectively and efficiently use your notification system at any point in the user journey. Making sure all of the common use cases are property documented is essential to accomplishing this.

*Example: At some point in the development of your application you will come across a notification use case that you did not  originally think of. Maybe a new notificaiton channel will emerge as important, or a new feature will emerge that requires a sophisticated notification flow.
An API that is well documented is the best way to guarantee that your product team will figure out new ways to delight your users and deliver on use-cases that you have not yet thought of.*

## Data/Analytics
Your internal team needs the ability to view the relevant data associated with your application’s notifications. They need to be able to answer questions around open rate, engagement rate, success rate, and other success criteria for different notifications across channels.

*Example: Notifications are an essential piece to effectively engaging your users. Having good data and analytics will allow you to invest more heavily in the channels and notifications that are working while fixing or dropping the ones that aren’t.*

## Robust Logs
Your team needs to ensure that deliverability is being achieved, as a message that does not make it to its destination is sure to fail in it’s goal. Logs need to not only serve the purpose of verifying deliverability, but should also make it easy to diagnose any deliverability issues quickly and efficiently.

*Example: Notifications are an essential piece to effectively engaging your users. Having good data and analytics will allow you to invest more heavily in the channels and notifications that are working while fixing or dropping the ones that aren’t.*

## Editing & Designing Notifications
As engineer’s we would prefer if all work was done via APIs, but actually designing the look and feel for notifications across various channels is better suited for some sort of web-based design tool. Not only does this allow for more granular control of the design, but it also allows non-technical team members to easily edit messages without needing to involve engineering. 

*Example: If you have a UI to build message templates that can be properly rendered across various channels such as email, SMS, and push you will make dramatically increase your teams agility (no longer need to deploy backend code to make copy changes to notifications) as remove a big burden from your engineering team (needing to respond to requests from marketing/content to change/update notifications).*


## Provider Abstraction
Abstracting the underlying email/SMS/push providers has several benefits. First it allows your developers to always interface with a consistent API, regardless of if the underlying vendor changes at some point. Secondly it creates the flexibility to utilize different providers for different use cases. 

*Example: Some SMS providers are dramatically cheaper in certain regions than others and certain email providers have much better deliverability in certain regions than others. With provider abstraction you could utilize the best provider for the job rather than relying on a single provider for all your users/use cases.*

## Centralization
As your product and engineering team scales, there will inevitably be different product teams with different focuses. Allowing every team to use the same notification system will not only help with your product velocity but will create a more consistent user experience for your users across the different areas of your product.

*Example: If your backend engineering team is using one system to create notifications and your growth engineering team is using another it will be nearly impossible to avoid a disjointed UX as well as tech debt associated with the different systems.*

