# Personalised SpamFilter using Social Network #
A personalised spam filter that enhances basic Bayesian filter by consuming user interests and social closeness to detect spam. Sender's activity determines his 'trustworthiness' and every users' trust scores are adapted accordingly. Spammer monitoring system keeps track of the trust scores and notifies users if a spammer is found in the immediate network of the user. This idea is based on the paper ["SOAP: A Social network Aided Personalized and effective spam filter to clean your e-mail box," 2011 Proceedings IEEE INFOCOM, Shanghai, 2011"](http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5934984&isnumber=5934870)

## Main components: ##
1. Basic Bayesian filter
2. Social closeness based filtering
3. Social interest based filtering
4. Adaptive trust management system
5. Friend Notification System

## Getting Started ##


* Install Microsoft Visual Studio
* Install Google api for getting Gmail contacts. Required dlls are:
              * Google.GData.Apps.dll
              * Google.GData.Client.dll
              * Google.GData.Contacts.dll
              * Google.GData.Extensions.dll
* Download Facebook Graph API files in PHP and Javascript( Facebook PHP SDK v4.1)
* To retrieve emails from users' mailbox use EagetMail. It provides the necessary POP3 and IMAP4 components.
* SwiftMailer for sending email notifications

References section provides links that will help in installation and configuration of above steps.

# References
[Plan for spam](http://www.paulgraham.com/spam.html)


