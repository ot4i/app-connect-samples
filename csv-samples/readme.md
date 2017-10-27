# CSV Parser Node Samples
## General instructions
This directory contains examples of the use of the CSV Parser node in App Connect integrations.
Each example comes with a brief description of the scenario covered, and a flow file that implements the scenario.

You'll find the following resources useful for all of them
* [How to use the CSV Parser Node](https://developer.ibm.com/integration/blog/2017/10/18/how-to-use-the-csv-parser-node-in-app-connect/)
* [How to upload integration flow files](https://developer.ibm.com/integration/blog/2017/09/29/exporting-importing-flows-ibm-app-connect/)

## Use-cases
### CSV file from Box used to add/update contacts to Salesforce
#### Overview
In this scenario, an App Connect flow exposes an API that
allows you to identify a file in box via its file URL.
The file contains a table of 'contact' details, which is used to
update contact information in salesforce.

#### To-do list
1. Upload your CSV file to Box
  * You can use `samplecontacts.csv` to get started
2. Upload the flow file `CSV-File-in-Box-to-Salesforce-contacts.yaml` (see *Resources* below)
  * This will create a new integration, which you will see in the App Connect dashboard
3. Open the newly created application
  * Review the configuration of each node, so that you understand how it has been configured
  * If you do not already have a connection to Box - Click on the Box node, and connect to Box
  * If you do not already have a connection to Salesforce - Click on the Salesforce node, and connect to Salesforce
4. Save and start the integration
5. Click on the 'manage' tab for your API, and set up the API authentication
  * Near the bottom of the page, you'll see a link to a dedicated 'API Portal' for consumers of your API to use
6. View your file on Box - and copy the file URL from the browser
7. Open up the API Portal for your API, and use the UI to 'try out' invoking your new API
  * Copy the file URL from box into the API input shown

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
* Completed integration flow file: `CSV-File-in-Box-to-Salesforce-contacts.yaml` (which you can [upload to your App Connect account](https://developer.ibm.com/integration/blog/2017/09/29/exporting-importing-flows-ibm-app-connect/))
