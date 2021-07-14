# Internal User Experience Requirements
![Intro Illustration](img/internal-user-experience.jpg?raw=true)

## API First
The nature of application-human-communication (aka notifications) is that they will need to be triggered from code. Because of this it’s important that as many features as possible that you offer in your system are able to be performed via that API.

## Great Documentation
It’s important that both your engineering team and non-technical users are able to effectively and efficiently use your notification system at any point in the user journey. Making sure all of the common use cases are property documented is essential to accomplishing this.

## Data/Analytics
Your internal team needs the ability to view the relevant data associated with your application’s notifications. They need to be able to answer questions around open rate, engagement rate, success rate, and other success criteria for different notifications across channels.

## Robust Logs
Your team needs to ensure that deliverability is being achieved, as a message that does not make it to its destination is sure to fail in it’s goal. Logs need to not only serve the purpose of verifying deliverability, but should also make it easy to diagnose any deliverability issues quickly and efficiently.


## Editing & Designing Notifications
As engineer’s we would prefer if all work was done via APIs, but actually designing the look and feel for notifications across various channels is better suited for some sort of web-based design tool. Not only does this allow for more granular control of the design, but it also allows non-technical team members to easily edit messages without needing to involve engineering. 


## Provider Abstraction
Abstracting the underlying email/SMS/push providers has several benefits. First it allows your developers to always interface with a consistent API, regardless of if the underlying vendor changes at some point. Secondly it creates the flexibility to utilize different providers for different use cases. 


## Centralization
As your product and engineering team scales, there will inevitably be different product teams with different focuses. Allowing every team to use the same notification system will not only help with your product velocity but will create a more consistent user experience for your users across the different areas of your product.

