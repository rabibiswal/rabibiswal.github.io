---
layout: post
title: Adapter Design Pattern
---

#### What is adapter pattern?
A ***structural design pattern*** which is used to make existing classes work with other (incompatible) classes without modifying source code of existing classes, by allowing interface of existing classes to be used as another interface.

#### The definition sucks, can you explain a bit more?
Well, let's think of a situation. You have a third-party library that reads a large piece of text(e.g. a blog) and gives you back a small summary of the content. This library can read and parse only English text. Your boss asked you to use it to read 13 Indian languages (Hindi, Telugu, Kannada etc.).

After few rounds of discussion with your colleagues, you come up with the following solution

- You are going to write a translator that would read local text and converts them to English.
- The English text can now be fed into the third-party library to get the summary
- The translator also converts the summary back to local language

pretty simple :)

However, you never realized, this is where Adapter design pattern neatly fits into, until your boss points it out.

#### Can you explain me with a diagram ?

Let's first take a look at the components used in this pattern

1. Adaptee - The existing interface with which the client wants to interact with
2. Adapter - The interface to be used by Adaptee
3. Target - The interface to be used by Client
4. Client  - The client that wants to use the Adaptee

Here is the UML of Adapter design pattern :

!["Adapter UML"](adapter-pattern.gif "Adapter UML")

Now lets take the above example and map them to these components to see a clear picture.

!["Adapter UML"](adapter-pattern-2.gif "Adapter UML")

As you see, essentially, **Adapters** are nothing but **Wrappers**.

#### Well, now I understand, but how can I explain it to my kid, who is learning programming?
Let's take another real-world example.

!["Adapter UML"](adapter-real-world.jpg "Adapter UML")

You have a mobile phone. You too have a power bank. Mobile phone needs to use power bank to get charged.
Here, your mobile phone becomes *client* and your power bank becomes *adaptee*. But now see, power bank has a USB port to connect to, but the mobile phone has a micro usb port for charging. Here you need a connector that can connect both mobile phone and power bank, that is essentially, the *adapter*. You can visualize *target* as the *specification* and *adapter* as the *implementation*.

If you translate it to an UML, this should look something similar to

!["Adapter UML"](adapter-pattern-3.gif "Adapter UML")

#### Where is it used within .NET Framework? Can you give me one example?
In .NET framework, adapter pattern is used as

- OleDbDataAdapter - suitable for use with any data source exposed by an OLE DB provider.
- SqlDataAdapter - specific to SQL Server.
- OdbcDataAdapter - optimized for accessing ODBC data sources.
- OracleDataAdapter - optimized for accessing Oracle databases.

#### What are the benefits of Adapter pattern?

1. Well, as you see the client is not dependent on the adaptee itself. So, changes to the adaptee only affects the adapter, not the client directly. (Imagine the USB port is moved from the bottom of the power bank to left side of it.)

2. You can make two incompatible objects work together

#### Do you have some code samples to look at?
Yes, you can take a look at the github repo -
https://github.com/rabinarayanb/DesignPattern.

#### Are there any other secrets, I need to learn about this pattern to master it?
Yes, a little bit :)

1. There are two types of adapter pattern implementations people generally use
	-	Object Adapter Pattern

		Here, the adapter holds a reference to the adaptee (above examples show object adapter pattern), favoring *composition*.   

	- Class Adapter Pattern

		Here, you create the adapter by implementing the *target interface* as well as inthering from *adaptee class*, favoring *inheritance*.

		However, if you want to create a adaptor targeting multiple adaptees (see below image), you can only use object adapter pattern, since multiple inheritance is not supported by some object-oriented languages.


	!["Adapter UML"](multi-adapter.jpg "Adapter UML")
2. Repository pattern (a high level design pattern) is a common use of Adapter pattern.
3. Adapter pattern is sometimes used with Strategy pattern.
4. Please note that, in may scenario, you'll find not a single pattern fits into your requirement. You'll have to use learn and use multiple patterns in order to rightly design and implement a solution.
5. Practice, Practice and Practice. Try to identify the patterns used in your existing code.When you start designing/writing a component, pause for a while, figure out if this fits into any design pattern.  You'll master it for sure.
