# Log4J-Patched
Log4J 2.0 beta9 without JNDI lookup functionality

## How does the Log4J exploit work?
A server sends the user a specially crafted packet which will be inducted into the logger info or error channel. 
When a message contains the wildcard ${jndi:ldap/...}, Log4J would try to resolve that to a java class and execute in memory.
This is a problem as the class has full access to all computer utilities with same permissions as the running application.

## How did we fix it?
We removed code that allows the resolving and instantiation of these wildcard statements completely eliminating the risk of connecting to third party servers or being exposed to specially crafted packets.
