# Personalised SpamFilter using Social Network #
A personalised spam filter that enhances basic Bayesian filter by consuming user interests and social closeness to detect spam. Sender's activity determines his 'trustworthiness' and every users' trust scores are adapted accordingly. Spammer monitoring system keeps track of the trust scores and notifies users if a spammer is found in the immediate network of the user. This idea is based on the paper ["SOAP: A Social network Aided Personalized and effective spam filter to clean your e-mail box," 2011 Proceedings IEEE INFOCOM, Shanghai, 2011"](http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5934984&isnumber=5934870)

## Main components: ##
1. Basic Bayesian filter
2. Social closeness based filtering
3. Social interest based filtering
4. Adaptive trust management system
5. Friend Notification System

## Getting Started ##

### Prereqisites ###
* Install Microsoft Visual Studio
* Install Google api for getting Gmail contacts. Required dlls are:
              * Google.GData.Apps.dll
              * Google.GData.Client.dll
              * Google.GData.Contacts.dll
              * Google.GData.Extensions.dll
* Download Facebook Graph API files in PHP and Javascript( Facebook PHP SDK v4.1)
* To retrieve emails from users' mailbox use EagetMail. It provides the necessary POP3 and IMAP4 components.
* SwiftMailer for sending email notifications
* MySQL

### Installing ###

1. https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio?view=vs-2017
2. https://developers.google.com/gdata/articles/dotnet_client_lib
3. https://developers.facebook.com/docs/graph-api/
4. https://developers.facebook.com/docs/reference/php/
5. https://www.emailarchitect.net/eagetmail
6. https://www.emailarchitect.net/eagetmail/sdk/
7. https://swiftmailer.symfony.com/docs/introduction.html
8. https://dev.mysql.com/doc/refman/8.0/en/installing.html

## How it works ##

### Bayesian Filtering ###
We start with one corpus of spam and one of The algorithm counts the number of times each token  occurs in each corpus. So we have 2 dictionaries with words and their counts. A third hash table is maintained that stores the probability of a word occuring in a spam mail. To avoid false positives, certain thressholds are decided by empirical observations like considering oly those words that occur atleast twice, double all the numbers in good. Detailed explanation at [Plan for spam](http://www.paulgraham.com/spam.html)

### Closeness based Filtering ###
Closeness is defined by the social distance(hops) between 2 users in a social network. The basic idea being friends send more relevant emails, thus lowering the chances of it being spam. User needs to authorize the retrieval of Gmail contacts so that the probababilty of email can be tuned. If the sender is not present in the reciever's contact list probability of email being spam is increased.

### Interest based Filtering ###
To gather user interests, Facebook Graph API is used. The graph API represents every user as a node and forms edges between other objects. These objects posts, comments, etc. JSON file can be extracted which has tags that distinguish the object types( Entertainment, Football, Books, etc). Its HTTP based that follows request-response procedure. The API also prevents privacy invasion as the users are asked to (de)select access/permissions when they log into the app.

### Trust Adaptation ###

Every user in the system has a trust score. Every legitimate email increases the score linearly and decreases the score exponentially when a spam mail is sent. 
Initially each of the users’ are given a trust value of 1.
T(user, friend)=a(T(user, friend)); 0<a<1 when mail received is spam 
T(user, friend)=T(user, friend) + b; 0<b<1 when mail received is legitimate
Factors ‘a’ and ‘b’ have been decided experimentally.

### Friend Notification System ###

When the trust score of an user falls below threshold, he is declared a spammer. People socially close to the spammer are notified via email. SwiftMailer helps to send mail over SMTP from localhost. The SwiftMailer framework offers a lot of classes which helps send personalized notifications to lot of people at a time from within the application.

## References ##
* [Plan for spam](http://www.paulgraham.com/spam.html)
* [nbayes](https://archive.codeplex.com/?p=nbayes)
* [Bayesian Filter in C#](https://www.codeproject.com/Articles/23472/%2FArticles%2F23472%2FA-Naive-Bayesian-Spam-Filter-for-C)
* https://www.sciencedirect.com/science/article/pii/S0925231215002106
* https://pdfs.semanticscholar.org/53f1/c0d27bcffd3cb8c72e475a2aad97154a74d6.pdf
* [Login with Facebook](https://www.phpvideoacademy.com/login-with-facebook-and-php-mysql/)



