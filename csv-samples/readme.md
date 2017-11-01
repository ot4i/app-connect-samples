# CSV Parser Node Samples
## General instructions
This directory contains examples of the use of the CSV Parser node in App Connect flows.
Each example comes with a brief description of the scenario covered, and a flow file that implements the scenario.

You'll find the following resources useful for all of them
* [How to use the CSV Parser Node](https://developer.ibm.com/integration/blog/2017/10/18/how-to-use-the-csv-parser-node-in-app-connect/)
* [How to import a flow into IBM App Connect](https://developer.ibm.com/integration/blog/2017/09/29/exporting-importing-flows-ibm-app-connect/)

## Use-cases
### CSV file from Box used to add/update contacts to Salesforce
#### Overview
In this scenario, an App Connect flow exposes an API that
allows you to identify a file in box via its file URL.
The file contains a table of 'contact' details, which is used to
update contact information in Salesforce.

#### To-do list
1. Upload your CSV file to Box
  * You can use `samplecontacts.csv` to get started
2. In App Connect, import the flow file `CSV-File-in-Box-to-Salesforce-contacts.yaml` (see *Resources* below)
  * This creates a new flow for an API, which opens to the `Properties` tab
3. Click on the `Operations` tab and then on `Edit Flow`
  * Review the configuration of each node, so that you understand how it has been configured
    * If you do not already have a connection to Box - Click on the Box node, and click `Connect to Box`
    * If you do not already have a connection to Salesforce - Click on the Salesforce node, and click `Connect to Salesforce`
    * Click on the CSV parser node to review the settings
4. Click `Done` to save the changes to your flow
  * You then can select 'Start API' from the more options menu (&#8942;) next to "Stopped"
5. Click on the `Manage` tab for your API, and set up the API authentication
  * You can leave this as the default `Require applications to authenticate via API Key`
  * To try the sample,
    1. Scroll down to 'Sharing Outside of Bluemix Organization'
    2. Click `Create API Key` and then copy the API key that is created.
7. Open up the API Portal for your API, and use the UI to 'try out' invoking your new API
   1. Click the `API PORTAL LINK` link.
   2. To explore your API in the portal and invoke it, click `Try it`
   3. Paste in the API Key that you just copied into the `X-IBM-Client-ID` field
   4. View your file on Box - and copy the file URL from the browser
   3. For the Parameter 'data', click `Generate` to create the API request body template, and then replace the value of the `fileurl` field with the URL that you just copied from box - for example;
     ```json
     {
       "fileurl": "https://app.box.com/file/123456789"
     }
     ```
   4. Click `Call operation`
     * Under Response, you should see `Code: 201 Created`
     * In the Response body, you should see the fileURL parameter used
     * If you Switch to your Salesforce account, you should see two new Contacts created from the CSV file:

#### Flow Details
##### Extracting the file ID from the file URL

The flow implements an API that allows the caller to specify a CSV file using its Box URL. The Box file URL is just the URL that you see in your browser URL bar when looking at a box file. The file URL has the general form;
```
https://app.box.com/file/<file-id>
```
where `<file-id` is a unique number.

In the sample flow, the `Box` retrieve node is used to retrieve the file contents. It only needs the file identifer - so this is extracted from the URL using a JSONata snippet;
```
{{$split($Request.fileurl, "/")[-1]}}
```
* `$Request.fileurl` is the file URL passed in by the REST API invocation
* The `$split()` function takes the URL and 'splits' it into an array, using the `/` character as a delimeter, to produce;
``` json
[
  "https:",
  "",
  "app.box.com",
  "file",
  "<file-id>"
]
```
* `[-1]` identifies the last element of the array - the file identifier


### Resources;
* [Video showing how to build the flow](https://www.youtube.com/watch?v=ypNH-gSu03I)
* Example CSV file: `samplecontacts.CSV`
* Completed flow file: `CSV-File-in-Box-to-Salesforce-contacts.yaml` (which you can [upload to your App Connect account](https://developer.ibm.com/integration/blog/2017/09/29/exporting-importing-flows-ibm-app-connect/))
