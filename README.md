# Email Notification Script for Ubiquiti Edge Router

This script is the implementation of the idea presented in [this](https://community.ui.com/questions/EdgeRouter-WAN-Failover-Email-Alert/d00d4332-6d39-472d-9cfd-3a4faf41f9b4) Unifi community post. It sends notification email whenever the WAN status changes in a dual WAN load-balancing scenario.

It has been tested successfully on EdgeRouter X v2.0.9.

This script should be added to `/config/scripts` and made executable:

```
chmod +x /config/scripts/wannotify
```

It uses sSMTP for sending emails. The configuration file of sSMTP located at `/etc/ssmtp/ssmtp.conf` should be modified as given [here](https://github.com/nasirhafeez/ubnt-er-email/blob/main/ssmtp.conf). This script uses Gmail for sending emails. You would need to enable Less Secure Apps in [Settings](https://myaccount.google.com/lesssecureapps). for the sending Gmail account.

The following command should be used to configure it as a load-balance transition script:

```
configure

set load-balance group G transition-script /config/scripts/wannotify

commit; save
```

Instructions for running scripts on Edge Routers are given [here](https://gist.github.com/nasirhafeez/9a2b9d236eaa48fc6d482f8aee603145)
