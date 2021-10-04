# namespace access
### Documentation
---
<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li>
    <a href="#setup--usage">Setup & Usage</a>
    <ul>
        <li><a href="#validating-the-session-token">Validating the Session Token</a></li>
        <li><a href="#getting-user-information">Getting User Information</a></li>
    </ul>
    </li>
    <li>
    <a href="#security">Security</a>
    <ul>
        <li><a href="#data-collection-policy">Data Collection Policy</a></li>
    </ul>
    </li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## Setup & Usage
Setting up namespace access logins on your website is super simple.
The only thing you need to do is to reference to our page by using the following url.

**OAuth URL**: `https://access.namespace.media`

In order to create a valid OAuth URL, you will need to add a `redirect_url`.
We recommend to use some type of `/callback` route, where you can process responses from our site.

**Example OAuth URL**: `https://access.namespace.media?redirect_url=https://example.com/callback`

In this use case, `example.com` would have a dedicated page, which validates & saves the `sessionToken`, which will be handed over as soon as the user authorized your login request.

### Validating the Session Token
After successfully getting authorized by the user, we will redirect back to your page, which you configured with `redirect_url`.

Our redirect URL will be something like this: `<redirect_url>?sessionToken=<token>`

**Example redirect URL**: `https://example.com/callback?sessionToken=thisTokenIsntWhatTokenLookLikeButYouKindaGetTheIdea`


Using this `sessionToken`, you can then send a `GET` to our backend API, which will reveal info about the user to you. A Session Token expires every 7 Days after initially created after a successful user login, which means, that you'll need to get authorized by the user every week.

### Getting User Information
*GET* to `https://kazu.namespace.media/me/<sessionToken>`

**Response**
```json
{
    "userId": "String" ,
    "email": "String"
}
```

Our API will reveal the User's ID and E-Mail to the holder of the Session Token, so we recommend keeping this token on the User's side of things only. 
In order to identify your site's user accounts, you can use the given `userId`, which is completely static and won't change under any circumstances.

# Security
**Access** Accounts are stored securily and with constant maintenance.
All traffic between our sites & services is highly encrypted, which makes it impossible, to perform most types of attacks on a user's data. We also ensure, that access given to third-party sites is revoked frequently, to avoid security risks and data leaks to unauthorized services.
While we think, security is most important, we also focus on exposing & collection as less data as possible. This means, that we won't ever collect data about the users of **namespace access** and we limit exposed data to third-parties a lot.

### Data Collection Policy
Third-Parties are not permitted to save data exposed by our API indefinetly, which aren't required to establish a working account system.
For example, Third-Parties may save User IDs to use them for their own identification of accounts, but E-Mails, Usernames or Tokens aren't considered required for this, so Third-Parties may delete them after a given amount of time or when it has been changed by the user.

# Contact
If you're a large Partner interested in using **namespace access** for other purposes than currently available, please contact us via `contact@namespace.media`.

For Developers & Users, please use our Support Contact Options in order to get in touch with us.

Via Mail: `support@namespace.media`</br>
Via Twitter: `https://twitter.com/namespacemedia`</br>
Via Discord: `https://discord.gg/6385g6T`
