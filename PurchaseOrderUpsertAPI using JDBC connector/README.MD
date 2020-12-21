# App Connect Samples for Blog "Using IBM App Connect in a containerised environment to interact with Java Database Connectivity"

Sample code and snippets that are referenced from the Blog [Using IBM App Connect in a containerised environment to interact with Java Database Connectivity](https://community.ibm.com/community/user/middleware/blogs/ibm-integration-id-team1/2020/10/16/using-jdbc-in-ibm-app-connect?CommunityKey=77544459-9fda-40da-ae0b-fc8c76f0ce18&tab=recentcommunityblogsdashboard)

If you find issues with the sample, please add a comment to the Blog, or use the support mechanisms to [contact the IBM App Connect team](https://developer.ibm.com/integration/support-ibm-integration/#tabappconnect)

## Scenario

Acme Corp can use the JDBC application node in App Connect to build an API to interact with these databases spread across different departments to query an order and insert or update an order if necessary. The integration flow can be exposed as an API that can be invoked by other applications be it their e-commerce website widgets or mobile applications. The API will update an order if any changes are made, such as adding new items or updating the quantity of existing items. If the order does not exist then it will create a new one.
