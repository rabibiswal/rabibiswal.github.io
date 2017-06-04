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

	This method has one drawback, however. Integrated Authentication works only with in organization's network boundary and not every machine can be joined to a organization's network e.g. 
	- Shared systems (may create security issues)
	- lack of necessary infrastructure etc.
	
- **Claim Based Authentication**
	With the increased need for cross-organization collaboration `Identity Providers` came into picture. An Identity Provider is a trusted entity across applications of different networks. This brings few interesting topics. How do applications with in local network identify an Identity Provider?With heterogeneous network infrastructures, how do applications accepts a legitimate user who claims to be authenticated by Identity Provider? 

	First, application has to `trust` the Identity Provider (this process is done offline by a process call app registration).

	Then comes the usage of `Token`. A token is a special string that is digitally signed by Identity Provider. 

	>Two popular token formats are SAML(Security Assertion Markup Language) and JWT(JSON Web Token). SAML is basically a XML style token format, where as, JWT is JSON based.
	
	A token contains, `Claims` (attributes of user's identity).

	Claim based authentication introduced bunch of protocols. Two populars are `SAML` and `WS-Federation`.

- **OAuth 1.0**
	OAuth emerged from collaboration of different companies like Twitter,Google, Yahoo to eliminate the loopholes in Claim based authentication and to support growing user base on public Internet.

- **OAuth 2.0**
	
