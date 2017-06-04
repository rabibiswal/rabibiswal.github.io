---
layout: post
title: A Brief On Authentication Mechanism
tags: azure AAD authentication beginners
---

I'll take you though the history of authentication mechanism, quickly.

- **Password**
	Passwords are the crudest authentication mechanism which has a very strong presence till date. There are, however, many issues associated with using passwords : 

	- They can be cracked or leaked
	- They can be easily forgotten
	- Managing passwords for multiple applications is difficult
	
- **Integrated Authentication**
	With the advent of local networks and increased need for modeling business processes through IT departments, `organization user account` came into picture. `Domain Controller` and `Active Directory` played very crucial role on Integrated Authentication or SSO (Single Sign On) i.e. once an user logs into the domain-joined machine through organization account, applications in the intranet allow appropriate access to the user.

	This method has one drawback, however. Integrated Authentication works only with in organization's network boundary. This made it difficult to use Integrated Authentication for scenario where partners of an organization wants access to applications with in organization's network, shared systems (due to security issues) and where there is a lack of necessary infrastructure etc.
	
- **Claim Based Authentication**
	With the increased need for cross-organization collaboration `Identity Providers` came into picture. An Identity Provider is a trusted entity across applications of different networks. This brings few interesting topics. How do applications with in local network identify an Identity Provider?With heterogeneous network infrastructures, how do applications accepts a legitimate user who claims to be authenticated by Identity Provider? 

	First, application has to `trust` the Identity Provider (this process is done offline by a process call app registration).

	Then comes the usage of `Token`. A token is a special string that is digitally signed by Identity Provider. 

	>Two popular token formats are SAML(Security Assertion Markup Language) and JWT(JSON Web Token). SAML is basically a XML style token format, where as, JWT is JSON based.
	
	A token contains, `Claims` (attributes of user's identity).

	Claim based authentication introduced bunch of protocols. Two popular protocols are `SAML` and `WS-Federation`.

- **OAuth 1.0**
	OAuth emerged from collaboration of different companies like Twitter, Google, Yahoo to eliminate the loopholes in protocols like SAML or Kerberos and to support growing user base on public Internet.

	OAuth 1.0 had few flaws.

	The use of SSL(Secure Sockets Layer) between the parties during authorization flow was not mandatory. Even, use of cryptographic functions are a part of the protocol, which made difficult for the developers to implement it. Such issues laid down the path to OAuth 2.0.  


- **OAuth 2.0**
	The OAuth 2.0 specification is fully named "The OAuth 2.0 Authorization Framework". OAuth 2.0 came up with many improvements and covered many scenario not addressed by OAuth 1.0. Unfortunately, OAuth 2.0 is not backward compatible with OAuth 1.0.

	Some of the benefits of OAuth 2.0

	- Improved API Security
	- Auth flow across internal applications
	- Authorization delegation
	- Federated identity
	- Easy service monitoring

	OAuth offered a great solution for authorizing server-to-server access to resources (i.e. cross domain SSO). But as mentioned earlier, there was another growing need. The need of the consumer web to be able to reuse the same account to sign in to multiple apps (e.g. today you can connect to may web application using Google or Facebook account). This need brought `OpenID` into the picture.

- **OpenID** `Open ID` and it's successor `OpenID 2.0` was an attempt to overcome the difficulties described 	earlier. However, OpenID and openID 2.0 are deprecating gradually due to difficulty in their implementation.

	Open ID 2.0 suffered from several design limitations. It assumed that Relying Parties could be web pages but not native applications. It also relied upon XML that led to adoption problems.

- **OpenID Connect**
	OpenID Connect is the third generation of OpenID technology that is backward compatible with OpenID 2.0. OpenID Connect adopted standard JSON Web Token (JWT) data structures, that made OpenID Connect dramatically easier for developers to implement.

	There are still few flaws found out in OAuth 2.0 and OpenId Connect as claimed by researchers. Hopefully there will be many more improvements coming up in near future.