# App Connect Samples for Blog "Using IBM Cloud Pak for Integration to configure a Kafka schema registry"

Sample code and snippets that are referenced from the Blog [Using IBM Cloud Pak for Integration to configure a Kafka schema registry](https://community.ibm.com/community/user/integration/blogs/divya-jha1/2021/05/18/configure-kafka-schema-registry-in-ibm-cp4i)

If you find issues with the sample, please add a comment to the Blog, or use the support mechanisms to [contact the IBM App Connect team](https://developer.ibm.com/integration/support-ibm-integration/#tabappconnect)

## Scenario

A company wants to build a lead management system to handle leads coming in from various channels with varying levels of interest in their products. The company's marketing team then wants to launch tailored marketing campaigns and nurture programs based on the leads’ category generated via various touchpoints. The leads can be generated via the company's website visitors, showroom walk-ins, social media campaigns, business partner-driven leads, and corporate partnership leads, etc. Due to the wide-ranging touchpoints, the details and structure of the data captured about leads can vary significantly. The leads need to be processed and classified into different buckets based on the marketing criteria and this information needs to be stored in the company's leads database.
The company has adopted Salesforce as their CRM to capture the leads and IBM Db2 is the back-end database where the final leads reside after classification. It is this leads data that will be used by marketing and sales teams for nurturing the leads to further stages of lead conversion. 

