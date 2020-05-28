## Why is the "from" address not one from our company and can we change this?

**There is a reason that the email “from” is [echosign@echosign.com](mailto:echosign@echosign.com) and it’s an important one.**

When a company sets up a domain like “adobe.com” there are [DNS](https://en.wikipedia.org/wiki/Domain_Name_System) records that point all calls to the adobe.com [domain](https://en.wikipedia.org/wiki/Domain_name) at one or more server IP addresses on the internet. There are also DNS- records for email that point to the email server/s for that domain.

**If we sent out the "default" emails from our echosign/Adobe Sign servers but added a “from” with an email domain that did NOT match those DNS records, the email domain in the email "from" would not resolve back to that domain’s email servers and the receiving email server would think that this was spam since this is a common way to try to “trick” people into thinking they got an email from a “known good” sender.**

 If customers want to use emails from Adobe to drive signing as well as reminders etc. we really can’t change the from address because all the emails for that account where we changed the “from” address would then get caught in the “spam/phishing” filters and recipient emails would not go through.

### Possible but complicated/high "level of effort" work-around

The only “work-around” to this issue is to suppress ALL the emails usually sent by our systems (API based or Account/Group/User Settings based suppression methods are available) and then configure a way for the info about the created agreements to be sent to some servers belonging to the customer (IE [webhooks](https://helpx.adobe.com/sign/using/adobe-sign-webhooks-api.html) or something like [MS Power Automate](https://docs.microsoft.com/en-us/connectors/adobesign/#when-a-new-agreement-is-created)). Those servers could use the agreement IDs to get the “signing URL” (via an [API call](https://documenter.getpostman.com/view/14752/Szf54VPJ?version=latest#9da8435e-4872-44ae-916d-a05435ba798a) or in a custom workflow action like the one for [Power Automate](https://docs.microsoft.com/en-us/connectors/adobesign/#retrieve-the-signing-url) ) for the created agreements and send emails from their own email servers that included the appropriate "action" (Please sign, Please Approve, etc.) links. The customer's systems would have to be configured to do the same for reminders and any other communications that typically come from our servers by default. This usually requires at least a lot of management using something like MS Flow/Power-Automate or, if that’s not available, a significant amount of custom development.

 Many of our customers ask for this  without understanding these complications and it’s really not necessary. We have thousands of companies all over the world that rely on billions of emails from our servers to drive recipient actions and all of them have our email in the “from” but the sender’s email address in the “reply to”.

