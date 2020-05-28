## Why is the "from" address not one from our company and can we change this?

**There is a reason that the email “from” is [echosign@echosign.com](mailto:echosign@echosign.com) and it’s an important one.**

When a company sets up a domain like “adobe.com” there are DNS records that point all calls to adobe.com at one or more server IP addresses on the internet. There are also DNS records for email that point to the email server/s for that domain.

**If we sent out emails from our echosign/Adobe Sign servers but added a “from” with an email domain that did NOT match those DNS records, the email domain in the email from would not resolve back to that domain’s email servers and the receiving email server would think that this was spam since this is a common way to try to “trick” people into thinking they got an email from a “known good” sender.**

 If customers want to use emails from Adobe to drive signing as well as reminders etc. we really can’t change the from address because all the emails for that account where we changed the “from” address would then get caught in the “spam/phishing” filters and recipient emails would not go through.

### Possible but complicated/high "level of effort" work-around

The only “work-around” to this issue is to suppress ALL the emails usually sent by our systems (API based or Account/Group/User Settings based) and then configure a way for the info about the sent agreements to be sent to some servers belonging to the customer. Those servers could use the agreement IDs to get the “signing URL” (via an API call or custom workflow action) for the created agreements and send emails from their own email servers that included the "action" links. The customers systems would have to do the same for reminders and any other communications that typically come from our servers by default. This usually requires at least a lot of management using something like MS Flow/Power-Automate or if that’s not available a significant amount of custom development.

 Many of our customers ask for this a lot without understanding these complications and it’s really not necessary. We have thousands of companies all over the world that rely on our emails to drive recipient actions and all of them have our email in the “from” but the sender’s email address in the “reply to”.

