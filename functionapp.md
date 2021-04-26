## FunctionApp

This is the code for the function app that can be deployed as an Azure Function.

It exposes the following endpoints:

* **Negotiate**: used by the client to connect to the signalr service.

* **OnConnected**: triggered when a client connects, it looks if there
  are still documents in the queue for this client and sends a print command
  for them if that is the case.
 
* **StartPrintJob**: triggered when a new document is created in blob storage,
  sends a print command to the client for that document.

* **DownloadPdf**: used by the client to download the pdf to process.

* **DeletePdf**: used by the client after downloading.

### Configuration

After deploying the Function App, some extra (1 time) configuration need to be done:

* Set the signalr connectionstring:
Under 'Function App > Configuration > Application settings' add a new application setting
with name `AzureSignalRConnectionString` and as value the connectionstring of the 
signalr service you want to use for this environment (e.g.: 
`Endpoint=https://serverlessprintingdev.service.signalr.net;AccessKey=<your access key>;Version=1.0;`.

* For the StartPrintJob trigger to work, create an event subscription:
  * Register Microsoft.EventGrid provider if it isn't already registered
  (`az provider register -n 'Microsoft.EventGrid'`).
  * Get the name of the function app (serverlessprintingdev).
  * Get the blobs_extension key from 'Function App > App keys'.
  * Create an event subscription ('Storage account > Events > Create Event
  Subscription') with name `PrintJobs` for 'Event Types' `Blob Created` 
  and with 'Endpoint Type' `Web Hook`.
  * Set the url for the web hook as 
  `https://<name of the funtion app>.azurewebsites.net/runtime/webhooks/blobs?functionName=StartPrintJob&code=<blobs_extension key>`.
  * Enable subject filtering (on the filters tab) and set 'Subject Begins With' to 
  `/blobServices/default/containers/print-jobs`.
 
* For the OnConnected trigger to work, under 'SignalR Service > Settings', 
add the following upstream url:
`http://<name of the funtion app>.azurewebsites.net/runtime/webhooks/signalr?code=<signalr_extension key>`. 
The signalr_extension key can be found under 'Function App > App keys'. 
Use `printhub` as 'Hub Rules', `connected` as 'Event Rules' and `connections` 
as 'Category Rules'
