## SQL Injection vs. Your Applications in the Modern Age

Developers dealing with web applications see a lot of things threatening to harm the things they build. Some of these things include attacks targeted at people (for example, social engineering), some of these attacks (DoS or DDoS attacks, Cross-Site Scripting, Cross-Site Request Forgery, Broken Authentication, Sensitive Data Exposure, Broken Access Control, Insecure Deserialization, etc.) target parts of web applications. However, some attacks primarily target your database and data stored there—one of such attacks is SQL injection (SQLi for short). In this blog post, we will look at the impacts such an attack might have.

<hr>

# Contents

1.  [What is SQL Injection and Why Is It Dangerous?](#what-is-sql-injection-and-why-is-it-dangerous) 
2. [How Does SQL Injection Work?](#how-does-sql-injection-work)
3. [Types of SQL Injection](#types-of-sql-injection) 
4. [Protecting Your Application from SQL Injection](#protecting-your-application-from-sql-injection) 
5. [Protecting Your Database from SQL Injection](#protecting-your-database-from-sql-injection) 
6. [Summary](#summary) 

<hr>
# What is SQL Injection and Why Is It Dangerous?

SQL injection is an attack frequently targeted at web applications. The purpose of such an attack frequently is to exfiltrate sensitive data from the database and use it for the personal gain of the attacker. Such an attack is so prevalent and dangerous precisely because many developers overlook the importance of security when creating public, web-facing solutions. When security gaps are overlooked, malicious parties often find and exploit them. These nefarious actors exploit such vulnerabilities because they can profit from selling data stolen during the breach.

The impacts of such an attack depend on your web application. Suppose your application does not store sensitive information, in which case, the attack would likely not have any far-reaching consequences. However, if that’s not the case, you might have a serious problem on your hands—sensitive data could be stolen and sold off for profit, causing issues for your business and needless problems for your customers due to stress resetting passwords and changing information elsewhere.

# How Does SQL Injection Work?

The concept of SQL injection is pretty simple: such an attack works because some developers put everything that the user writes in a given input field into a query and pass it on to a database. A basic snippet of vulnerable code would look like this (you can also use $_GET instead of $_POST, the premise is the same):

`$Input = $_POST['input'];`

`SELECT * FROM demo_table WHERE column [= | < | > | <= | >= | LIKE ...] '$Input';`

As you can see, in some of the cases, the vulnerable code is pretty simple (it can also get complex, we will get into different scenarios later) – such vulnerable code is then exploited by attackers frequently using the quote character (') to induce errors. Once it induces errors, attackers know the code is vulnerable, and they can attack our applications.

# Types of SQL Injection

There are a couple of categories that SQL injection attacks fall under:

- **Classic SQL injection** – a basic SQL injection type when the attacker aims to execute SQL code inside a database to gain access to an application or any other system that has implemented MySQL into its database architecture.
- **Union-based SQL injection** – a SQL injection type where an attacker uses the UNION clause in MySQL to combine the results of queries which returns a response useful for the attacker.
- **Error-based SQL injection** – a type of SQL injection where the attacker gathers data mainly through error messages being displayed (or absent) on the application that is being attacked. Error-based SQL injection has a few types in and of itself.
- **Out-of-band (OOB) SQL injection** – a type of SQL injection where an attacker cannot use the same application for both attacking and result gathering. A lesser-known type of SQL injection, but a type nonetheless.

Attackers use each of the types outlined above to accomplish different goals – classic SQL injection is useful if the attacker has some implied knowledge about the inner workings of the system, union-based SQL injection can be useful if the attacker combines the results of a couple of `SELECT` statements into a single result set, error-based SQL injection is used when the application is "silent" (meaning that it doesn’t return any responses, so the attacker looks for functionality changes when issuing certain kinds of queries)

# Protecting Your Application from SQL Injection

At this point, you should have a pretty good understanding of what SQL injection is and what its types are, but how do you protect your applications from such an attack? Thankfully, there are a couple of well-known ways to lessen the risk of such a vulnerability being exploited now or in the future:

- **Keep all of your application components up to date and install all of the necessary security patches** – keeping application components up to date should be an effective first line of defense against any attack.
- **Validate input** – as the success of such an attack heavily depends on the input that the attacker provides to the system, input validation could be another successful way to prevent SQL injection attacks now and in the future.
- **Use parameterized statements** – the usage of parameterized statements is perhaps the most effective way of defending against SQL injection attacks. When parameterized statements are in use, the server always interprets user input as a value and does not parse it. For example:  

    ```sql
/* Prepare MySQL statement */

  if (!($statement = $mysqli->prepare(
      "SELECT customerID 
      FROM orders 
      WHERE item = ?"
      ))) {
          echo "Failed: (" . $mysqli->errno . ") " . $mysqli->error;
  }

  /* 
  Bind variables to statement as parameters using bind_param().
  The type (first) parameter can take integers (i), doubles (d), 
  strings(s), and blobs (b).
  */

  $purchasedItem = 'ice cream';
  if (!$statement->bind_param("s", $purchasedItem)) {    
      echo "Failed: (" . $statement->errno . ") " . $statement->error;
  }

  /* Execute prepared MySQL statement */
  if (!$statement->execute()) {
      echo "Failed: (" . $statement->errno . ") " . $statement->error;
  }
```  

- **Use a web application firewall** – using a web application firewall (WAF) is another effective line of defense because web application firewalls are usually able to identify and block multiple types of attacks, including SQL injection, Cross-Site Scripting, Cross-Site Request Forgery, Broken Access Control, Sensitive Data Exposure, DoS, or DDoS attacks amongst others. A web application firewall should ideally be used with parameterized statements for maximum efficiency and defense against SQL injection and other types of attacks.

- **Use security-focused applications provided by MySQL or other vendors** – MySQL offers a way to protect your applications against SQL injection on the enterprise level by using a MySQL Enterprise Firewall tool, which can provide real-time protection against database-specific threats. Additionally, several other vendors are worth discussing further (aside from MySQL, some of them include MariaDB, MinervaDB, MongoDB, Oracle, Severalnines, and others). Still, for this blog post, we aren’t going to go too much into detail.

- **Avoid granting administrative privileges when they might not be necessary** – avoiding granting unnecessary privileges can be an effective fortress against many kinds of attacks, including privilege escalation and, of course, SQL injection. For example, if the user using your application only needs certain access rights, consider only granting the necessary permissions to complete tasks. Enforcing the least privilege rule on the database level is also an excellent idea.

Keeping these points in mind should help keep your application humming along nicely.

# Protecting Your Database from SQL Injection

Using prepared statements, using security-focused plugins provided by MySQL, avoiding granting unnecessary administrative privileges, and taking other aforementioned precautions into account should put you and your database on a good path. However, if you want to dig deeper into MySQL and understand why SQL queries work the way they do and why using a, for example, web application firewall (WAF) might protect you against many kinds of attacks, including SQL injection, consider this:

- Think of each query as a big task that is composed of smaller tasks.
- The tasks of the query can be observed by running `SHOW PROFILE FOR QUERY [query id here];`

If used correctly, in most cases, the output will provide you with what the query did and the duration of the task. You will also be able to observe a bunch of interesting things, including getting answers to questions like:

- How long did the query take to start?
- How long did the query take to check for permissions?
- How much time did it take for MySQL to open tables?
- How much time did it take for MySQL to initialize processes?
- How much time did it take for MySQL to optimize, prepare and (or) execute the query?
- How much time did it take for MySQL to send the data back to you to be viewed?
- How much time did it take for MySQL to end the query, close tables, free up items?

Some of the answers to these questions might help you understand why SQL injection works the way it does. For example, issue a `SHOW PROFILE FOR QUERY` query again, and you will see the following:

![image-1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1636018905593/A_WgLf5yi.png)
The marked row indicates that straight after starting to run the query, MySQL checks for permissions. Remember what we discussed earlier? You should avoid granting unnecessary privileges precisely for this reason – if the MySQL account that an attacker is targeting does not have enough permissions, the query will fail. Since the functionality of the `SHOW PROFILE FOR QUERY` queries aren’t in the scope in this blog post, we aren’t going to go into too much detail here, but you can see how and why following the advice above is important.

Most of the advice outlined above is also applicable in the database space:

- Keeping all of your application components up to date includes phpMyAdmin.
- Validating input includes validating all of the input, not only validating input that is part of something.
- Parameterized statements can (and should) be used in all occasions where SQL queries are used to avoid data exfiltration from certain tables.
- Using a web application firewall and using security-focused plugins might prevent attackers from gaining access to your database.
- Avoiding granting too many privileges might also save your database from disaster (refer to the example above)  

Take the advice above into account, and you should be well on the way towards mitigating SQL injection issues that might strike your database now or in the future.

# Summary

As you might tell, most of the advice helping you secure your applications and databases from SQL injection is pretty general and straightforward. However, securing your databases from SQL injection is not rocket science either – keep the guidelines that have been outlined above in mind, and you should be good to go!

Hope you learned something new today!

Don't hesitate to comment below to raise any queries or suggestions.

Will see you guys very very soon!! :)