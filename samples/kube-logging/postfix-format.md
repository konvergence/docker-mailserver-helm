see  https://github.com/winebarrel/fluent-plugin-filter-parse-postfix



* sample log accepted
```
Jun 22 04:00:28 smtp-docker-mailserver-7d69ff5b88-qrwqn postfix/smtp[312720]: A18EE1005090: to=<frederic.gourlin@bnpparibas.com>, relay=smtp-in-internet-usr-m.gslb.srv.bnpparibas[155.140.74.36]:25, delay=2.3, delays=0.29/0.06/0.74/1.2, dsn=2.0.0, status=sent (250 ok:  Message 256429218 accepted)
```


* sample log bounced
```
Jun 22 08:26:31 smtp-docker-mailserver-7d69ff5b88-qrwqn postfix/smtp[380470]: 4D489100508D: to=<no-reply-unknown@xxx.com>, relay=xxx-com.mail.protection.outlook.com[104.47.2.36]:25, delay=0.38, delays=0.02/0.01/0.22/0.13, dsn=5.4.1, status=bounced (host xxx-com.mail.protection.outlook.com[104.9.8.9] said: 550 5.4.1 Recipient address rejected: Access denied. AS(201806281) [DB5EUR01FT088.eop-EUR01.prod.protection.outlook.com 2023-06-22T08:26:31.592Z 08DB72B25E50380B] (in reply to RCPT TO command))
```



```
{
  "time":"Feb 27 09:02:38",
  "hostname":"MyHOSTNAME",
  "process":"postfix/smtp[26490]",
  "queue_id":"5E31727A35D",
  "to":"*********@myemail.net",
  "domain":"myemail.net",
  "relay":"gateway-f1.isp.att.net[204.127.217.17]:25",
  "conn_use":2,
  "delay":0.58,
  "delays":"0.11/0.03/0.23/0.20",
  "dsn":"2.0.0",
  "status":"sent",
  "status_detail":"(250 ok ; id=en4req0070M63004172202102)"
}
```

list of status: 
status=sent
status=deferred
status=bounced
status=expired



# sample status detail : for sent

(250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as A18EE1005090)
(250 ok:  Message 256429218 accepted)

# sample status detail : for bounced
(host xxxxx-com.mail.protection.outlook.com[104.x.y.z] said: 550 5.4.1 Recipient address rejected: Access denied. AS(201806281) [DB5EUR01FT088.eop-EUR01.prod.protection.outlook.com 2023-06-22T08:26:31.592Z 08DB72B25E50380B] (in reply to RCPT TO command))