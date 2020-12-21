# App Connect Samples for Blog "Using IBM App Connect to interact with Kafka"

Sample code and snippets that are referenced from the Blog [Using IBM App Connect to interact with Kafka](https://community.ibm.com/community/user/middleware/blogs/nidhi-modi1/2020/12/14/using-ibm-app-connect-to-interact-with-kafka?CommunityKey=77544459-9fda-40da-ae0b-fc8c76f0ce18&tab=recentcommunityblogsdashboard)

If you find issues with the sample, please add a comment to the Blog, or use the support mechanisms to [contact the IBM App Connect team](https://developer.ibm.com/integration/support-ibm-integration/#tabappconnect)

## Scenario

Scenario 1: 
A subscriber of a mobile service, uses App X to manage his profile. In said App X they perform such actions as updating addresses, telephone numbers, purchasing new add-on services and upgrading plans etc. All of these events from App X stream to Kafka as immutable events. These events/messages are picked up and updated in the customer's profile of a mobile customer database.

Scenario 2: 

The customer support team in Acme airlines has been tasked with tracking the latest airline information. Once this information has been received they need to contact the relevant departments with the latest flight updates in under 1 minute after the impact has been identified.
Salesforce is used to capture airline information for Acme airlines so to implement this scenario in App Connect we are going to use a custom user defined object in Salesforce called "AirInfo". 
