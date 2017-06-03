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
	
- **Claim Based Identity**
	With the increased need for cross-organization collaboration `Identity Providers` came into picture. An Identity Provider is a trusted entity across applications of different networks.