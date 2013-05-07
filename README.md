confluence-jmeter
=================

The original files are available on Atlassian [web site](https://confluence.atlassian.com/display/JIRA/Performance+Testing+Scripts).

I updated the script, based on version [4.2.2](https://maven.atlassian.com/content/repositories/atlassian-public/com/atlassian/confluence/testing/jmeter/performance-testing/), by fixing some issue and adding new features.

The script needs some fixes:

1. it doesn't save the session on the Remote API and then operations like Create Personal Space and Grant View on Personal Space fail to connect because of the rpc token
2. the labels used as tags in Confluence are not the same (we used demonstration and sales)
3. the Browse User Status operation has an incomplete Response Assertion
4. When deleting  the space, operation that can take some time,  the script doesn't wait in a loop so it can't remove some users and also when deleting a space Confluence doesn't go back to the Dashboard but instead stays on the page

Further I improved the script giving the possibility:

1. to create users from Crowd, using a new command line parameter -Jenable.sso=true, which is false by default
2. to use https in case Confluence is setup with https instead of http, using a new command like parameter -Jconfluence.protocol=https, which is http by default

Therefore after you download the script (with the resources) just remember to adapt the Crowd configuration (parameter -Jcrowd.host), that the operation Create User from Crowd expect to have Crowd under the same ip address of Confluence (you can of course change it) and be careful when modifying (from Read Only to Ready Write) the connection to Crowd.

The script has been executed on Confluence 4.3.1 with Jmeter 2.7 and Confluence 5.0.2 with Jmeter 2.9

